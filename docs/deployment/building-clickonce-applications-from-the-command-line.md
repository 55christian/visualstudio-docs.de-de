---
title: Erstellen von ClickOnce-Anwendungen über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcab7ac3bb2a7983d8500b6f27f910fa33fc1efe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929155"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Erstellen von ClickOnce-Anwendungen über die Befehlszeile
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], Sie können Projekte über die Befehlszeile erstellen, selbst wenn sie in der integrierten Entwicklungsumgebung (IDE) erstellt werden. In der Tat können Sie ein Projekt erstellt wurde, mit neu erstellen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] auf einem anderen Computer, der nur die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert. Dadurch können Sie einen Build mit einem automatisierten Prozess zu reproduzieren, z. B. in einer zentralen Labor- oder mithilfe von erweiterten Skriptingverfahren würde den Rahmen der Erstellung des Projekts selbst.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Verwenden von MSBuild, um Bereitstellung von ClickOnce-Anwendungen zu reproduzieren.
 Wenn Sie Msbuild an der Befehlszeile Veröffentlichungsordner, weist er das MSBuild-System zum Erstellen des Projekts, und erstellen Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung im Ordner "Publish". Dies entspricht dem Auswählen der **veröffentlichen** Befehl in der IDE.

 Dieser Befehl führt *msbuild.exe*, d.h. auf den Pfad in der Umgebung der Visual Studio-Eingabeaufforderung.

 Ein "Ziel" ist ein Indikator dafür, dass MSBuild zum Verarbeiten des Befehls. Die wichtigsten Ziele sind das Ziel "Build" und das Ziel "publish". Das Build-Ziel ist das Äquivalent zur Auswahl des Builds-Befehl (oder drücken Sie F5), in der IDE. Wenn Sie nur das Projekt erstellen möchten, können Sie diese erreichen, die durch Eingabe `msbuild`. Dieser Befehl funktioniert, da das Build-Ziel als Standardziel für alle Projekte, die vom [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Dies bedeutet, dass Sie nicht explizit benötigen, geben Sie das Build-Ziel. Aus diesem Grund geben `msbuild` den gleichen Vorgang wie das Eingeben von `msbuild /target:build`.

 Die `/target:publish` weist MSBuild an das Veröffentlichungsziel aufrufen. Das Veröffentlichungsziel hängt von der Build-Ziel. Dies bedeutet, dass der Veröffentlichungsvorgang eine Obermenge des Buildvorgangs. Z. B. Wenn Sie auf eine der quellcodeverwaltung für Ihre Visual Basic oder C#-Dateien eine Änderung vorgenommen haben, wird die entsprechende Assembly automatisch durch den Veröffentlichungsvorgang neu erstellt werden.

 Weitere Informationen zum Generieren einer vollständiges [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung über das Befehlszeilentool "Mage.exe" zum Erstellen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest, finden Sie unter [Exemplarische Vorgehensweise: Manuelles bereitstellen eine ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Erstellen und eine einfache ClickOnce-Anwendung mit MSBuild erstellen

#### <a name="to-create-and-publish-a-clickonce-project"></a>Erstellen und Veröffentlichen einer ClickOnce-Projekt

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

    Wählen Sie die **Windows-Desktopanwendung** -Projektvorlage aus, und nennen Sie das Projekt `CmdLineDemo`.

1. Von der **erstellen** Menü klicken Sie auf die **veröffentlichen** Befehl.

    Dadurch wird sichergestellt, dass das Projekt ordnungsgemäß konfiguriert ist, erzeugt eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anwendungsbereitstellung.

    Der Webpublishing-Assistent wird angezeigt.

1. Klicken Sie im Assistenten für das Veröffentlichen auf **Fertig stellen**.

    Visual Studio generiert und zeigt die Standardwebseite wird aufgerufen, *Publish.htm*.

1. Speichern Sie das Projekt, und notieren Sie sich den Speicherort des Ordners, in dem es gespeichert ist.

   Erstellen Sie die oben genannten Schritte eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Projekt, das zum ersten Mal veröffentlicht wurde. Jetzt können Sie den Build außerhalb der IDE reproduzieren.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Zum Reproduzieren des Builds über die Befehlszeile

1. Beenden Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Aus dem Windows **starten** im Menü klicken Sie auf **Programme**, klicken Sie dann **Microsoft Visual Studio**, klicken Sie dann **Visual Studio-Tools**, und klicken Sie dann **Visual Studio-Eingabeaufforderung**. Im Stammordner des aktuellen Benutzers sollte eine Eingabeaufforderung geöffnet werden.

3. In der **Visual Studio-Eingabeaufforderung**, wechseln Sie zum Speicherort des Projekts, das Sie soeben erstellt, weiter oben haben. Geben Sie beispielsweise Folgendes ein: `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. So entfernen Sie die vorhandenen Dateien in der erstellten "zum Erstellen und Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Projekt" Typ `rmdir /s publish`.

    Dieser Schritt ist optional, aber es wird sichergestellt, dass die neuen Dateien von der Befehlszeile erzeugt wurden.

5. Geben Sie `msbuild /target:publish` ein.

   Die oben genannten Schritte erzeugt eine vollständige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anwendungsbereitstellung in einem Unterordner des Projekts mit dem Namen **veröffentlichen**. *CmdLineDemo.application* ist die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Der Ordner *CmdLineDemo_1.0.0.0* enthält die Dateien *CmdLineDemo.exe* und *CmdLineDemo.exe.manifest*, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. *Setup.exe* ist der Bootstrapper, die standardmäßig konfiguriert ist, installieren die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Der Ordner DotNetFX enthält die verteilbaren Komponenten für die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Dies ist der gesamte Satz von Dateien, die Sie Ihre Anwendung über das Internet oder über UNC-Pfad oder CD/DVD bereitstellen müssen.

## <a name="publish-properties"></a>Eigenschaften veröffentlichen
 Wenn Sie die Anwendung in den oben genannten Verfahren veröffentlichen, werden die folgenden Eigenschaften in der Projektdatei, durch den Veröffentlichungs-Assistenten eingefügt. Diese Eigenschaften direkt beeinflussen, wie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung erzeugt wird.

 Unter *CmdLineDemo.vbproj* / *CmdLineDemo.csproj* ist Folgendes möglich:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Sie können eine dieser Eigenschaften in der Befehlszeile überschreiben, ohne die Projektdatei selbst zu ändern. Beispielsweise wird Folgendes erstellt die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anwendungsbereitstellung, ohne den Bootstrapper:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Veröffentlichungseigenschaften werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der **veröffentlichen**, **Sicherheit**, und **Signierung** Eigenschaftenseiten der **Projekt-Designer** . Im folgenden finden Sie eine Beschreibung der die Veröffentlichungseigenschaften, sowie einen Überblick darüber, wie jede in den verschiedenen Eigenschaftenseiten der Anwendungs-Designer festgelegt wird:

- `AssemblyOriginatorKeyFile` Bestimmt die Schlüsseldatei zum Signieren Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifeste. Dieser Schlüssel kann auch verwendet werden, Ihre Assemblys einen starken Namen zuweisen. Diese Eigenschaft wird festgelegt, auf die **Signierung** auf der Seite die **Projekt-Designer**.

  Die folgenden Eigenschaften werden festgelegt, auf die **Sicherheit** Seite:

- **Aktivieren von ClickOnce-Sicherheitseinstellungen** bestimmt, ob [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste generiert werden. Wenn ein Projekt erstmalig erstellt wird, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestgenerierung ist standardmäßig deaktiviert. Der Assistent wird automatisch aktivieren Sie dieses Flag auf, wenn Sie sich zum ersten Mal veröffentlichen.

- **TargetZone** bestimmt die Ebene der Vertrauenswürdigkeit in ausgegeben werden Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Mögliche Werte sind "Internet", "LocalIntranet" und "Benutzerdefiniert". Internet und LocalIntranet bewirkt, dass einen Standardberechtigungssatz, der in ausgegeben werden Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. LocalIntranet ist die Standardeinstellung, und es bedeutet im Grunde volle Vertrauenswürdigkeit. Benutzerdefinierte gibt an, dass nur die Berechtigungen explizit angegeben wird, in der Basisklasse *"App.manifest"* sind, dass die Datei ausgegeben werden, in der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest. Die *"App.manifest"* Datei ist eine partielle Manifestdatei, die nur die Definitionen der Vertrauensstellung Informationen enthält. Es ist eine versteckte Datei, die automatisch zu Ihrem Projekt hinzugefügt werden, wenn Sie Berechtigungen konfigurieren, die sich auf die **Sicherheit** Seite.

  Die folgenden Eigenschaften werden festgelegt, auf die **veröffentlichen** Seite:

- `PublishUrl` ist der Speicherort, in der IDE, in dem die Anwendung veröffentlicht wird. Dieser wird eingefügt, in der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest, wenn weder die `InstallUrl` oder `UpdateUrl` -Eigenschaft angegeben wird.

- `ApplicationVersion` Gibt die Version des der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dies ist eine vierstellige Versionsnummer. Wenn die letzte Ziffer ist ein "*", die `ApplicationRevision` durch ersetzt, den Wert, der zum Zeitpunkt der Erstellung in das Manifest eingefügt.

- `ApplicationRevision` Gibt die Version an. Dies ist eine ganze Zahl, wobei jedes Mal erhöht wird, die Sie in der IDE veröffentlichen. Beachten Sie, dass für Builds ausgeführt werden, an der Befehlszeile nicht automatisch erhöht wird.

- `Install` Bestimmt, ob die Anwendung eine installierte Anwendung oder eine Anwendung über das Web ausgeführt wird.

- `InstallUrl` (nicht dargestellt) ist der Speicherort, in dem Benutzer die Anwendung installiert wird. Wenn angegeben, wird dieser Wert geschrieben, in der *setup.exe* Bootstrapper Wenn die `IsWebBootstrapper` -Eigenschaft aktiviert ist. Es wird auch in die Manifestdatei bei der Anwendung eingefügt der `UpdateUrl` nicht angegeben ist.

- `SupportUrl` (nicht dargestellt) ist der Speicherort in verknüpft die **Programme hinzufügen/entfernen** im Dialogfeld für eine installierte Anwendung.

  Die folgenden Eigenschaften werden festgelegt, der **Anwendungsupdates** klicken Sie im Dialogfeld auf das Sie über die **veröffentlichen** Seite.

- `UpdateEnabled` Gibt an, ob die Anwendung nach Updates suchen soll.

- `UpdateMode` Gibt an, entweder Updates im Vordergrund oder im Hintergrund erfolgen.

- `UpdateInterval` Gibt an, wie häufig die Anwendung nach Updates suchen soll.

- `UpdateIntervalUnits` Gibt an, ob die `UpdateInterval` Wert wird in Einheiten von Stunden, Tage oder Wochen.

- `UpdateUrl` (nicht dargestellt) ist der Speicherort, der die Anwendung aus dem Updates erhält. Wenn angegeben, wird dieser Wert in das Anwendungsmanifest eingefügt.

- Die folgenden Eigenschaften werden festgelegt, der **Veröffentlichungsoptionen** klicken Sie im Dialogfeld auf das Sie über die **veröffentlichen** Seite.

- `PublisherName` Gibt den Namen des Verlegers in der Eingabeaufforderung angezeigt, wenn die Installation oder Ausführung der Anwendung angezeigt. Im Falle einer installierten Anwendung, es wird auch zum Geben Sie den Namen des Ordners auf dem **starten** Menü.

- `ProductName` Gibt den Namen des Produkts in die Eingabeaufforderung angezeigt, wenn die Installation oder Ausführung der Anwendung angezeigt. Im Falle einer installierten Anwendung, es wird auch zum Geben Sie den Namen der Verknüpfung auf die **starten** Menü.

- Die folgenden Eigenschaften werden festgelegt, der **Voraussetzungen** klicken Sie im Dialogfeld auf das Sie über die **veröffentlichen** Seite.

- `BootstrapperEnabled` Bestimmt, ob generiert die *setup.exe* Bootstrapper.

- `IsWebBootstrapper` Bestimmt, ob die *setup.exe* Bootstrapper funktioniert nur über das Internet oder in datenträgerbasierte-Modus.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL, and UpdateURL
 Die folgende Tabelle zeigt die vier URL-Optionen für die ClickOnce-Bereitstellung.

|URL-option|Beschreibung|
|----------------|-----------------|
|`PublishURL`|Erforderlich, wenn Sie die ClickOnce-Anwendung auf einer Website veröffentlichen.|
|`InstallURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn der Standort für die Installation unterscheidet die `PublishURL`. Sie könnten z. B. Festlegen der `PublishURL` auf einem FTP-Pfad und der `InstallURL` an eine Web-URL.|
|`SupportURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn die Support-Website unterscheidet die `PublishURL`. Sie können z. B. Festlegen der `SupportURL` auf die Customer-Website Ihres Unternehmens.|
|`UpdateURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn der Updatepfad unterscheidet die `InstallURL`. Sie könnten z. B. Festlegen der `PublishURL` auf einem FTP-Pfad und der `UpdateURL` an eine Web-URL.|

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce security and deployment (ClickOnce-Sicherheit und -Bereitstellung)](../deployment/clickonce-security-and-deployment.md)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)