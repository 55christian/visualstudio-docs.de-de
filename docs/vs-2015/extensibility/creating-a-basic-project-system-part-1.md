---
title: Erstellen eines grundlegenden Projekt Systems, Teil 1 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295486"
---
# <a name="creating-a-basic-project-system-part-1"></a>Erstellen eines grundlegenden Projektsystems, Teil 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio sind Projekte die Container, mit denen Entwickler Quell Code Dateien und andere Ressourcen organisieren. Projekte werden in der **Projektmappen-Explorer**als untergeordnete Elemente der Projektmappen angezeigt. Mit Projekten können Sie Quellcode organisieren, erstellen, Debuggen und bereitstellen und Verweise auf Webdienste, Datenbanken und andere Ressourcen erstellen.  
  
 Projekte werden in Projektdateien definiert, z. b. eine CSPROJ-Datei für C# ein visuelles Projekt. Sie können einen eigenen Projekttyp erstellen, der über eine eigene Projektdatei Namen Erweiterung verfügt. Weitere Informationen zu Projekttypen finden Sie unter [Projekttypen](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Wenn Sie Visual Studio mit einem benutzerdefinierten Projekttyp erweitern müssen, wird dringend empfohlen, das [Visual Studio-Projekt System](https://github.com/Microsoft/VSProjectSystem) zu nutzen, das eine Reihe von Vorteilen gegenüber der Erstellung eines Projekt Systems von Grund auf bietet:  
> 
> - Einfacheres Onboarding.  Selbst bei einem einfachen Projekt System sind Zehntausende von Codezeilen erforderlich.  Durch die Nutzung von CPS werden die onboardingkosten auf einige wenige Klicks reduziert, bevor Sie diese an Ihre Anforderungen anpassen können.  
>   - Einfachere Wartung.  Durch die Verwendung von CPS müssen Sie nur Ihre eigenen Szenarien einhalten.  Wir behandeln die Wartung der gesamten Projekt Systeminfrastruktur.  
> 
>   Wenn Sie Versionen von Visual Studio, die älter als Visual Studio 2013 sind, als Zielversion verwenden müssen, können Sie CPS nicht in einer Visual Studio-Erweiterung nutzen.  Wenn dies der Fall ist, ist diese exemplarische Vorgehensweise ein guter Ausgangspunkt für den Einstieg.  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einen Projekttyp erstellen, der die Projektdatei Namen Erweiterung. MyProj enthält. Diese exemplarische Vorgehensweise basiert auf dem vorhandenen C# visuellen Projekt System.  
  
> [!NOTE]
> Ein End-to-End-Beispiel für ein umfassendes Sprachprojekt System finden Sie unter dem IronPython-Beispiel Deep Dive in den [VSSDK-Beispielen](../misc/vssdk-samples.md).  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie diese Aufgaben ausführen:  
  
- Erstellen Sie einen grundlegenden Projekttyp.  
  
- Erstellen Sie eine einfache Projektvorlage.  
  
- Registrieren Sie die Projektvorlage bei Visual Studio.  
  
- Erstellen Sie eine Projekt Instanz, indem Sie das Dialogfeld **Neues Projekt** öffnen und dann die Vorlage verwenden.  
  
- Erstellen Sie eine projektfactory für das Projekt System.  
  
- Erstellen Sie einen Projekt Knoten für das Projekt System.  
  
- Fügen Sie benutzerdefinierte Symbole für das Projekt System hinzu.  
  
- Implementieren Sie die grundlegende Vorlagen Parameter Ersetzung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Außerdem müssen Sie den Quellcode für das [verwaltete Paket Framework für Projekte](https://archive.codeplex.com/?p=mpfproj12)herunterladen. Extrahieren Sie die Datei an einen Speicherort, der für die Lösung zugänglich ist, die Sie erstellen möchten.  
  
## <a name="creating-a-basic-project-type"></a>Erstellen eines grundlegenden Projekt Typs  
 Erstellen Sie C# ein VSIX-Projekt mit dem Namen **simpleproject**. (**Datei, neu, Projekt** und dann  **C#, Erweiterbarkeit, Visual Studio-Paket**). Fügen Sie eine Visual Studio-Paket-Projekt Element Vorlage hinzu (Klicken Sie auf dem Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus, und navigieren Sie zu **Erweiterbarkeit/Visual Studio-Paket**). Nennen Sie die Datei **simpleprojectpackage**.  
  
## <a name="creating-a-basic-project-template"></a>Erstellen einer grundlegenden Projektvorlage  
 Nun können Sie dieses grundlegende VSPackage ändern, um den neuen Projekttyp ". MyProj" zu implementieren. Um ein Projekt zu erstellen, das auf dem Projekttyp. MyProj basiert, muss Visual Studio wissen, welche Dateien, Ressourcen und Verweise dem neuen Projekt hinzugefügt werden sollen. Um diese Informationen bereitzustellen, fügen Sie Projektdateien in einem Projektvorlagen Ordner ein. Wenn ein Benutzer das MyProj-Projekt verwendet, um ein Projekt zu erstellen, werden die Dateien in das neue Projekt kopiert.  
  
#### <a name="to-create-a-basic-project-template"></a>So erstellen Sie eine einfache Projektvorlage  
  
1. Fügen Sie dem Projekt drei Ordner hinzu, eine unter der anderen: **templates\project\simpleproject**. (Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten **simpleproject** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Geben Sie dem Ordner den Namen `Templates`anmelden. Fügen Sie im Ordner **Vorlagen** einen Ordner mit dem Namen `Projects`hinzu. Fügen Sie im **Projekt** Ordner einen Ordner mit dem Namen `SimpleProject`hinzu.)  
  
2. Fügen Sie im Ordner **project\simpleproject** eine Symbol Datei mit dem Namen `SimpleProject.ico`hinzu. Wenn Sie auf **Hinzufügen**klicken, wird der Symbol-Editor geöffnet.  
  
3. Machen Sie das Symbol unverwechselbar. Dieses Symbol wird später in der exemplarischen Vorgehensweise im Dialogfeld **Neues Projekt** angezeigt.  
  
    ![Symbol "einfaches Projekt"](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. Speichern Sie das Symbol, und schließen Sie den Symbol-Editor.  
  
5. Fügen Sie im Ordner **project\simpleproject** ein **Klassen** Element mit dem Namen `Program.cs`hinzu.  
  
6. Ersetzen Sie den vorhandenen Code durch die folgenden Zeilen.  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
  
   namespace $nameSpace$  
   {  
       public class $className$  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
   > [!IMPORTANT]
   > Dies ist nicht die endgültige Form des Program.CS-Codes. die Ersetzungs Parameter werden in einem späteren Schritt behandelt. Möglicherweise werden Kompilierungsfehler angezeigt, aber solange die **BuildAction** -Datei der Datei **Inhalt**ist, sollten Sie in der Lage sein, das Projekt wie gewohnt zu erstellen und auszuführen.  
  
7. Speichern Sie die Datei.  
  
8. Kopieren Sie die Datei AssemblyInfo.cs aus dem Ordner **Properties** in den Ordner **project\simpleproject** .  
  
9. Fügen Sie im Ordner **project\simpleproject** eine XML-Datei mit dem Namen `SimpleProject.myproj`hinzu.  
  
   > [!NOTE]
   > Die Dateinamenerweiterung für alle Projekte dieses Typs ist. MyProj. Wenn Sie Sie ändern möchten, müssen Sie Sie überall dort ändern, wo Sie in der exemplarischen Vorgehensweise erwähnt werden.  
  
10. Ersetzen Sie den vorhandenen Inhalt durch die folgenden Zeilen.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
11. Speichern Sie die Datei.  
  
12. Legen Sie im Fenster **Eigenschaften** die **Buildaktion** von AssemblyInfo.cs, Program.cs, simpleproject. ico und simpleproject. Myproj auf **Content**fest, und legen Sie Ihre include-Eigenschaft **in VSIX** -Eigenschaften auf **true**fest.  
  
    In dieser Projektvorlage wird ein einfaches C# visuelles Projekt beschrieben, das sowohl eine Debugkonfiguration als auch eine Releasekonfiguration aufweist. Das Projekt enthält zwei Quelldateien: AssemblyInfo.cs und Program.cs sowie mehrere Assemblyverweise. Wenn ein Projekt aus der Vorlage erstellt wird, wird der ProjectGuid-Wert automatisch durch eine neue GUID ersetzt.  
  
    In **Projektmappen-Explorer**sollte der Ordner erweiterte **Vorlagen** folgendermaßen aussehen:  
  
    Vorlagen  
  
    Projekte  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Erstellen einer grundlegenden projektfactory  
 Sie müssen Visual Studio den Speicherort Ihres Projektvorlagen Ordners mitteilen. Fügen Sie zu diesem Zweck der VSPackage-Klasse ein Attribut hinzu, das die projektfactory implementiert, sodass der Speicherort der Vorlage in die Systemregistrierung geschrieben wird, wenn das VSPackage erstellt wird. Beginnen Sie, indem Sie eine grundlegende projektfactory erstellen, die durch eine projektfactory-GUID identifiziert wird. Verwenden Sie das <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>-Attribut, um die projektfactory mit der simpleprojectpackage-Klasse zu verbinden.  
  
#### <a name="to-create-a-basic-project-factory"></a>So erstellen Sie eine grundlegende projektfactory  
  
1. Öffnen Sie SimpleProjectPackageGuids.cs im Code-Editor.  
  
2. Erstellen Sie GUIDs für Ihre projektfactory (Klicken Sie **im Menü Extras** auf **GUID erstellen**), oder verwenden Sie das im folgenden Beispiel. Fügen Sie die GUIDs der simpleprojectpackageguids-Klasse hinzu. Die GUIDs müssen sowohl das GUID-Formular als auch das Zeichen folgen Format aufweisen. Der resultierende Code sollte dem folgenden Beispiel ähneln.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Fügen Sie dem ersten **simpleproject** -Ordner mit dem Namen `SimpleProjectFactory.cs`eine Klasse hinzu.  
  
4. Fügen Sie die folgenden using-Anweisungen hinzu:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Fügen Sie der simpleprojectfactory-Klasse ein GUID-Attribut hinzu. Der Wert des-Attributs ist die neue projektfactory-GUID.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Nun können Sie Ihre Projektvorlage registrieren.  
  
#### <a name="to-register-the-project-template"></a>So registrieren Sie die Projektvorlage  
  
1. Fügen Sie in SimpleProjectPackage.cs der simpleprojectpackage-Klasse wie folgt ein <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>-Attribut hinzu.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt  
  
    Beim erneuten Erstellen wird die Projektvorlage registriert.  
  
   Die Parameter `defaultProjectExtension` und `possibleProjectExtensions` werden auf die Projektdatei Erweiterung (. MyProj) festgelegt. Der `projectTemplatesDirectory`-Parameter wird auf den relativen Pfad des Vorlagen Ordners festgelegt. Während des Builds wird dieser Pfad in einen vollständigen Build konvertiert und zur Registrierung hinzugefügt, um das Projekt System zu registrieren.  
  
## <a name="testing-the-template-registration"></a>Testen der Vorlagen Registrierung  
 Die Vorlagen Registrierung weist Visual Studio den Speicherort des Projektvorlagen Ordners an, damit Visual Studio den Vorlagen Namen und das Symbol im Dialogfeld **Neues Projekt** anzeigen kann.  
  
#### <a name="to-test-the-template-registration"></a>So testen Sie die Vorlagen Registrierung  
  
1. Drücken Sie F5, um das Debuggen einer experimentellen Instanz von Visual Studio zu starten.  
  
2. Erstellen Sie in der experimentellen Instanz ein neues Projekt für den neu erstellten Projekttyp. Im Dialogfeld **Neues Projekt** sollte **simpleproject** unter **installierte Vorlagen**angezeigt werden.  
  
   Nun verfügen Sie über eine projektfactory, die registriert ist. Es kann jedoch noch kein Projekt erstellt werden. Das Projektpaket und die projektfactory arbeiten zusammen, um ein Projekt zu erstellen und zu initialisieren.  
  
## <a name="add-the-managed-package-framework-code"></a>Hinzufügen des verwalteten Paket-Framework-Codes  
 Implementieren Sie die Verbindung zwischen dem Projektpaket und der projektfactory.  
  
- Importieren Sie die Quell Code Dateien für das verwaltete Paket Framework.  
  
    1. Entladen Sie das Projekt simpleproject (Klicken Sie in **Projektmappen-Explorer**auf den Projekt Knoten, und klicken Sie im Kontextmenü auf **Projekt entladen**.), und öffnen Sie die Projektdatei im XML-Editor.  
  
    2. Fügen Sie der Projektdatei die folgenden Blöcke hinzu (direkt oberhalb der \<> Blöcke importieren). Legen Sie projectbasepath auf den Speicherort der Datei projectbase. Files im verwalteten Paket Framework-Code fest, den Sie soeben heruntergeladen haben. Möglicherweise müssen Sie dem Pfadnamen einen umgekehrten Schrägstrich hinzufügen. Wenn Sie dies nicht tun, kann das Projekt möglicherweise den Code des verwalteten Paket-Frameworks nicht finden.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > Vergessen Sie nicht den umgekehrten Schrägstrich am Ende des Pfads.  
  
    3. Laden Sie das Projekt neu.  
  
    4. Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
        - Microsoft. VisualStudio. Designer. Interfaces (in \<VSSDK-Installation > \visualstudiointegration\common\assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>So initialisieren Sie die projektfactory  
  
1. Fügen Sie in der Datei SimpleProjectPackage.cs die folgende `using`-Anweisung hinzu.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Leiten Sie die `SimpleProjectPackage`-Klasse von `Microsoft.VisualStudio.Package.ProjectPackage`ab.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Registrieren Sie die projektfactory. Fügen Sie der `SimpleProjectPackage.Initialize`-Methode die folgende Zeile hinzu, unmittelbar nach `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Implementieren Sie die abstrakte Eigenschaften `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. Fügen Sie in SimpleProjectFactory.cs nach den vorhandenen `using`-Anweisungen die folgende `using`-Anweisung hinzu.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Leiten Sie die `SimpleProjectFactory`-Klasse von `ProjectFactory`ab.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Fügen Sie der `SimpleProjectFactory`-Klasse die folgende Dummy-Methode hinzu. Diese Methode wird in einem späteren Abschnitt implementiert.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Fügen Sie der `SimpleProjectFactory`-Klasse das folgende Feld und den folgenden Konstruktor hinzu. Diese `SimpleProjectPackage` Referenz wird in einem privaten Feld zwischengespeichert, sodass Sie zum Festlegen einer Dienstanbieter Site verwendet werden kann.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt  
  
## <a name="testing-the-project-factory-implementation"></a>Testen der projektfactory-Implementierung  
 Testen Sie, ob der Konstruktor für die projektfactory-Implementierung aufgerufen wird.  
  
#### <a name="to-test-the-project-factory-implementation"></a>So testen Sie die projektfactory-Implementierung  
  
1. Legen Sie in der Datei SimpleProjectFactory.cs einen Haltepunkt in der folgenden Zeile im `SimpleProjectFactory`-Konstruktor fest.  
  
    ```  
    this.package = package;  
    ```  
  
2. Drücken Sie F5, um eine experimentelle Instanz von Visual Studio zu starten.  
  
3. Beginnen Sie in der experimentellen Instanz mit dem Erstellen eines neuen Projekts. Wählen Sie im Dialogfeld **Neues Projekt** den Projekttyp simpleproject aus, und klicken Sie dann auf **OK**. Die Ausführung hält am Haltepunkt an.  
  
4. Löschen Sie den Haltepunkt, und beenden Sie das Debugging. Da wir noch keinen Projekt Knoten erstellt haben, löst der Projekt Erstellungs Code weiterhin Ausnahmen aus.  
  
## <a name="extending-the-project-node-class"></a>Erweitern der Projekt Knoten Klasse  
 Nun können Sie die `SimpleProjectNode`-Klasse implementieren, die von der `ProjectNode`-Klasse abgeleitet wird. Die `ProjectNode`-Basisklasse verarbeitet die folgenden Aufgaben der Projekt Erstellung:  
  
- Kopiert die Projektvorlagen Datei simpleproject. MyProj in den neuen Projektordner. Die Kopie wird entsprechend dem Namen umbenannt, der im Dialogfeld **Neues Projekt** eingegeben wurde. Der Wert der `ProjectGuid`-Eigenschaft wird durch eine neue GUID ersetzt.  
  
- Durchläuft die MSBuild-Elemente der Projektvorlagen Datei simpleproject. MyProj und sucht nach `Compile` Elementen. Für jede `Compile` Zieldatei wird die Datei in den neuen Projektordner kopiert.  
  
  Die abgeleitete `SimpleProjectNode` Klasse verarbeitet diese Aufgaben:  
  
- Ermöglicht das Erstellen oder auswählen von Symbolen für Projekt-und Datei Knoten in **Projektmappen-Explorer** .  
  
- Ermöglicht das Angeben zusätzlicher Projektvorlagen-Parameter Ersetzungen.  
  
#### <a name="to-extend-the-project-node-class"></a>So erweitern Sie die Projekt Knoten Klasse  
  
1. 
  
2. Fügen Sie eine Klasse mit dem Namen `SimpleProjectNode.cs`hinzu.  
  
3. Ersetzen Sie den vorhandenen Code durch folgenden Code:  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Project;  
  
   namespace SimpleProject  
   {  
       public class SimpleProjectNode : ProjectNode  
       {  
           private SimpleProjectPackage package;  
  
           public SimpleProjectNode(SimpleProjectPackage package)  
           {  
               this.package = package;  
           }  
           public override Guid ProjectGuid  
           {  
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
           }  
           public override string ProjectType  
           {  
               get { return "SimpleProjectType"; }  
           }  
  
           public override void AddFileFromTemplate(  
               string source, string target)  
           {  
               this.FileTemplateProcessor.UntokenFile(source, target);  
               this.FileTemplateProcessor.Reset();  
           }  
       }  
   }  
   ```  
  
   Diese Implementierung von `SimpleProjectNode` Klassen weist diese überschriebenen Methoden auf:  
  
- `ProjectGuid`, die die projektfactory-GUID zurückgibt.  
  
- `ProjectType`, der den lokalisierten Namen des Projekt Typs zurückgibt.  
  
- `AddFileFromTemplate`, das ausgewählte Dateien aus dem Vorlagen Ordner in das Ziel Projekt kopiert. Diese Methode wird in einem späteren Abschnitt weiter implementiert.  
  
  Der `SimpleProjectNode`-Konstruktor, wie der `SimpleProjectFactory`-Konstruktor, speichert einen `SimpleProjectPackage` Verweis in einem privaten Feld zur späteren Verwendung zwischen.  
  
  Um die `SimpleProjectFactory`-Klasse mit der `SimpleProjectNode`-Klasse zu verbinden, müssen Sie eine neue `SimpleProjectNode` in der `SimpleProjectFactory.CreateProject`-Methode instanziieren und in einem privaten Feld zur späteren Verwendung Zwischenspeichern.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>So verbinden Sie die projektfactoryklasse und die Node-Klasse  
  
1. Fügen Sie in der Datei SimpleProjectFactory.cs die folgende `using`-Anweisung hinzu:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Ersetzen Sie die `SimpleProjectFactory.CreateProject`-Methode, indem Sie den folgenden Code verwenden.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Erstellen Sie die Lösung neu, und überprüfen Sie, ob Sie fehlerfrei erstellt  
  
## <a name="testing-the-project-node-class"></a>Testen der Projekt Knoten Klasse  
 Testen Sie Ihre projektfactory, um festzustellen, ob eine Projekt Hierarchie erstellt wird.  
  
#### <a name="to-test-the-project-node-class"></a>So testen Sie die Projekt Knoten Klasse  
  
1. Drücken Sie die Taste F5, um mit dem Debuggen zu beginnen. Erstellen Sie in der experimentellen Instanz ein neues simpleproject.  
  
2. Visual Studio sollte Ihre projektfactory aufzurufen, um ein Projekt zu erstellen.  
  
3. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Hinzufügen eines benutzerdefinierten Projekt Knoten Symbols  
 Das Symbol für den Projekt Knoten im vorherigen Abschnitt ist ein Standard Symbol. Sie können Sie in ein benutzerdefiniertes Symbol ändern.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>So fügen Sie ein Symbol für einen benutzerdefinierten Projekt Knoten hinzu  
  
1. Fügen Sie im Ordner **Ressourcen** eine Bitmapdatei mit dem Namen simpleprojectnode. bmp hinzu.  
  
2. Reduzieren Sie im Fenster **Eigenschaften** die Bitmap auf 16 x 16 Pixel. Legen Sie die Bitmap als unverwechselbar dar.  
  
    ![Einfaches Projekt-comm](../extensibility/media/simpleprojprojectcomm.png "Simpleprojprojectcomm")  
  
3. Ändern Sie im **Eigenschaften** Fenster die **Buildaktion** der Bitmap in **Embedded Resource**.  
  
4. Fügen Sie in SimpleProjectNode.cs die folgenden `using`-Anweisungen hinzu:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Fügen Sie dem `SimpleProjectNode`-Klasse das folgende statische Feld und den folgenden Konstruktor hinzu.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Fügen Sie am Anfang der `SimpleProjectNode`-Klasse die folgende Eigenschaft hinzu.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Ersetzen Sie den Instanzkonstruktor durch den folgenden Code.  
  
   ```  
   public SimpleProjectNode(SimpleProjectPackage package)  
   {  
       this.package = package;  
  
       imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
       foreach (Image img in imageList.Images)  
       {  
           this.ImageHandler.AddImage(img);  
       }  
   }  
   ```  
  
   Während der statischen Konstruktion ruft `SimpleProjectNode` die Bitmap des Projekt Knotens aus den Assemblymanifestressourcen ab und speichert Sie zur späteren Verwendung in einem privaten Feld zwischen. Beachten Sie die Syntax des <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> bildrfad. Verwenden Sie die <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>-Methode, um die Namen der Manifestressourcen anzuzeigen, die in eine Assembly eingebettet sind. Wenn diese Methode auf die `SimpleProject` Assembly angewendet wird, sollten die Ergebnisse wie folgt lauten:  
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources. imagelis. bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Während der Instanzerstellung lädt die `ProjectNode` Basisklasse "Resources. imagelis. bmp", in der häufig verwendete 16 x 16-Bitmaps aus "resources\imagelis.bmp" eingebettet sind. Diese Bitmap-Liste wird `SimpleProjectNode` als imagehandler. ImageList zur Verfügung gestellt. `SimpleProjectNode` fügt der Liste die Bitmap des Projekt Knotens an. Der Offset der Bitmap für das Projekt Knoten in der Bildliste wird für die spätere Verwendung als Wert der Eigenschaft Public `ImageIndex` zwischengespeichert. Visual Studio verwendet diese Eigenschaft, um zu bestimmen, welche Bitmap als Projekt Knoten Symbol angezeigt werden soll.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testen des Symbol für den benutzerdefinierten Projekt Knoten  
 Testen Sie Ihre projektfactory, um zu sehen, ob Sie eine Projekt Hierarchie mit dem Symbol des benutzerdefinierten Projekt Knotens erstellt.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>So testen Sie das Symbol für den benutzerdefinierten Projekt Knoten  
  
1. Starten Sie das Debugging, und erstellen Sie in der experimentellen Instanz ein neues simpleproject.  
  
2. Beachten Sie im neu erstellten Projekt, dass simpleprojectnode. bmp als Symbol für den Projekt Knoten verwendet wird.  
  
     ![Simple Project New Project-Knoten](../extensibility/media/simpleprojnewprojectnode.png "Simpleprojnewprojectnode")  
  
3. Öffnen Sie Program.cs im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Beachten Sie, dass die Vorlagen Parameter $Namespace $ und $ClassName $ keine neuen Werte aufweisen. Im nächsten Abschnitt erfahren Sie, wie die Vorlagen Parameter Ersetzung implementiert wird.  
  
## <a name="substituting-template-parameters"></a>Ersetzen von Vorlagen Parametern  
 In einem früheren Abschnitt haben Sie die Projektvorlage mithilfe des `ProvideProjectFactory`-Attributs bei Visual Studio registriert. Wenn Sie den Pfad eines Vorlagen Ordners auf diese Weise registrieren, können Sie die grundlegende Vorlagen Parameter Ersetzung durch Überschreiben und Erweitern der `ProjectNode.AddFileFromTemplate`-Klasse aktivieren. Weitere Informationen finden Sie [unter New Project Generation: at the Hood, Part Two](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Fügen Sie jetzt der `AddFileFromTemplate`-Klasse Ersatz Code hinzu.  
  
#### <a name="to-substitute-template-parameters"></a>So ersetzen Sie Vorlagen Parameter  
  
1. Fügen Sie in der Datei SimpleProjectNode.cs die folgende `using`-Anweisung hinzu.  
  
   ```  
   using System.IO;  
   ```  
  
2. Ersetzen Sie die `AddFileFromTemplate`-Methode, indem Sie den folgenden Code verwenden.  
  
   ```  
   public override void AddFileFromTemplate(  
       string source, string target)  
   {  
       string nameSpace =   
           this.FileTemplateProcessor.GetFileNamespace(target, this);  
       string className = Path.GetFileNameWithoutExtension(target);  
  
       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
       this.FileTemplateProcessor.AddReplace("$className$", className);  
  
       this.FileTemplateProcessor.UntokenFile(source, target);  
       this.FileTemplateProcessor.Reset();  
   }  
   ```  
  
3. Legen Sie einen Haltepunkt in der-Methode direkt nach der `className` Zuweisungsanweisung fest.  
  
   Die Zuweisungs Anweisungen bestimmen angemessene Werte für einen Namespace und einen neuen Klassennamen. Durch die beiden `ProjectNode.FileTemplateProcessor.AddReplace` Methodenaufrufe werden die entsprechenden Vorlagen Parameterwerte durch die Verwendung dieser neuen Werte ersetzt.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testen der Vorlagen Parameter Ersetzung  
 Nun können Sie die Vorlagen Parameter Ersetzung testen.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>So testen Sie die Vorlagen Parameter Ersetzung  
  
1. Starten Sie das Debugging, und erstellen Sie in der experimentellen Instanz ein neues simpleproject.  
  
2. Die Ausführung wird am Haltepunkt in der `AddFileFromTemplate`-Methode angehalten.  
  
3. Überprüfen Sie die Werte für die Parameter `nameSpace` und `className`.  
  
   - `nameSpace` wird der Wert des \<RootNamespace->-Elements in der Projektvorlagen Datei "\templates\project\simpleproject\simpleproject.MyProj" zugewiesen. In diesem Fall lautet der Wert "myrootnamespace".  
  
   - `className` erhält den Wert des Klassen Quell Dateinamens ohne die Dateinamenerweiterung. In diesem Fall ist die erste Datei, die in den Zielordner kopiert werden soll, AssemblyInfo.cs; Daher ist der Wert von ClassName "AssemblyInfo".  
  
4. Entfernen Sie den Breakpoint und drücken Sie F5, um die Ausführung fortzusetzen.  
  
    Visual Studio sollte die Erstellung eines Projekts abschließen.  
  
5. Öffnen Sie Program.cs im Code-Editor. Es sollte Quellcode angezeigt werden, der dem folgenden Code ähnelt.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace MyRootNamespace  
   {  
       public class Program  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
    Beachten Sie, dass der Namespace jetzt "myrootnamespace" und der Klassenname jetzt "Program" lautet.  
  
6. Startet das Debuggen des Projekts. Das neue Projekt sollte "Hello VSX!!!" kompilieren, ausführen und anzeigen. im Konsolenfenster anzuzeigen.  
  
    ![Befehl "einfaches Projekt"](../extensibility/media/simpleprojcommand.png "Simpleprojcommand")  
  
   Herzlichen Glückwunsch! Sie haben ein grundlegendes verwaltetes Projekt System implementiert.
