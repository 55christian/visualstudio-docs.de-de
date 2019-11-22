---
title: Diagnostizieren von Problemen nach der Bereitstellung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b24cf97ef0768ee700841aa859698cd2307710
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298301"
---
# <a name="diagnose-problems-after-deployment"></a>Diagnostizieren von Problemen nach der Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Probleme mit der Webanwendung ASP.NET nach der Bereitstellung mit IntelliTrace zu diagnostizieren, geben Sie Buildinformationen zu Ihrer Version mit an, damit Visual Studio automatisch die richtigen Quelldateien und Symboldateien findet, die für das Debuggen des IntelliTrace-Protokolls erforderlich sind.  
  
 Wenn Sie Microsoft Monitoring Agent zur Steuerung von IntelliTrace verwenden, müssen Sie Application Performance Monitoring auf dem Webserver einrichten. Auf diese Weise werden Diagnoseereignisse beim Betrieb Ihrer App gesammelt und in einer IntelliTrace-Protokolldatei gespeichert. Anschließend können Sie die Ereignisse in Visual Studio Enterprise (nicht den Professional oder Community Editions) öffnen, zum Code springen, in dem ein Ereignis eingetreten ist, die aufgezeichneten Werte zum jeweiligen Zeitpunkt anzeigen und den ausgeführten Code vorwärts oder rückwärts durchlaufen. Nachdem Sie das Problem gefunden und behoben haben, wiederholen Sie den Zyklus zum Erstellen, Freigeben und Überwachen der Version, um zukünftige Probleme früher und schneller beheben zu können.  
  
 ![Code, build, release, monitor, diagnose, fix](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Sie benötigen Folgendes:**  
  
- Microsoft Visual Studio 2015 oder Team Foundation Server 2015, 2013, 2012 oder 2010 zum Erstellen Ihres Builds  
  
- Microsoft Monitoring Agent zum Überwachen der App und zum Aufzeichnen von Diagnosedaten  
  
- Visual Studio Enterprise (nicht Professional oder Community Editions) zum Anzeigen von Diagnosedaten und Debuggen Ihres Codes mit IntelliTrace  
  
## <a name="SetUpBuild"></a> Schritt 1: Aufnehmen der Buildinformationen in Ihre Version  
 Richten Sie den Buildprozess ein, um eine Buildmanifestdatei (BuildInfo.config) für Ihr Webprojekt zu erstellen und fügen Sie dieses Manifest in Ihre Version ein. Dieses Manifest enthält Informationen über Projekt, Quellcodeverwaltung und Buildsystem, die für die Erstellung einer bestimmten Version verwendet wurden. Mit diesen Informationen kann Visual Studio die entsprechenden Quellen und Symbole finden, nachdem Sie das IntelliTrace-Protokoll geöffnet haben, um die aufgezeichneten Ereignisse zu prüfen.  
  
### <a name="AutomatedBuild"></a> Erstellen des Buildmanifests für einen automatischen Buildvorgang mithilfe von Team Foundation Server  
 Führen Sie diese Schritte aus, egal ob Sie Team Foundation oder Git als Versionskontrolle verwenden.  
  
#### <a name="TFS2013"></a> Team Foundation Server 2013  
 Richten Sie Ihre Builddefinition so ein, dass diese den Ort Ihrer Quellen sowie Build und Symbole in das Buildmanifest (BuildInfo.config-Datei) schreibt. Team Foundation Build erstellt diese Datei automatisch und fügt sie in das Ausgabeverzeichnis Ihres Projekts ein.  
  
1. [Edit your build definition or create a new build definition.](https://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![View build definition in TFS 2013](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Wählen Sie die Standardvorlage (TfvcTemplate.12.xaml) oder eine eigene benutzerdefinierte Vorlage aus.  
  
    ![Choose build process template &#45; TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Geben Sie an, wo die Symboldatei (PDB) gespeichert werden soll, sodass die Quelle automatisch indiziert wird.  
  
    Wenn Sie eine benutzerdefinierte Vorlage verwenden, vergewissern Sie sich, dass die Vorlage über eine Aktivität zum Indizieren der Quelle verfügt. Später fügen Sie ein MSBuild-Argument hinzu, um anzugeben, wo die Symboldateien gespeichert werden sollen.  
  
    ![Set up symbols path in build definition TFS 2013](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Weitere Informationen über Symbole finden Sie unter [Veröffentlichen von Symboldaten](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Fügen Sie dieses MSBuild-Argument hinzu, um TFS und Symboldateispeicherorte zur Buildmanifestdatei hinzuzufügen:  
  
    **/p:IncludeServerNameInBuildInfo=True**  
  
    Jeder, der auf Ihren Webserver zugreifen kann, kann diese Speicherorte im Buildmanifest anzeigen. Achten Sie darauf, dass Ihr Quellserver sicher ist.  
  
5. Wenn Sie eine benutzerdefinierte Vorlage verwenden, fügen Sie dieses MSBuild-Argument hinzu, um anzugeben, wo die Symboldatei gespeichert werden soll:  
  
    **/p:BuildSymbolStorePath=** \<*Pfad zu Symbolen*>  
  
    ![Include build server info in build def TFS 2013](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    Fügen Sie der Webprojektdatei (CSPROJ oder VBPROJ) diese Zeilen hinzu:  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Führen Sie einen neuen Build aus.  
  
   **Schritt 2:** [Schritt 2: Release your app](#DeployRelease)  
  
#### <a name="TFS2012_2010"></a> Team Foundation Server 2012 oder 2010  
 Führen Sie die folgenden Schritte aus, um das Buildmanifest (BuildInfo.config) für Ihr Projekt automatisch zu erstellen und in das Ausgabeverzeichnis Ihres Projekts einzufügen. Die Datei erscheint als "*ProjektName*.BuildInfo.config" im Ausgabeverzeichnis, wird jedoch im Bereitstellungsverzeichnis als "BuildInfo.config" umbenannt, nachdem Sie Ihre App veröffentlicht haben.  
  
1. Installieren Sie eine beliebige Edition von Visual Studio 2013 auf Ihrem Team Foundation Build-Server.  
  
2. Geben Sie in Ihrer Builddefinition an, wo die Symbole gespeichert werden sollen, sodass die Quelle automatisch indiziert wird.  
  
    Wenn Sie eine benutzerdefinierte Vorlage verwenden, vergewissern Sie sich, dass die Vorlage über eine Aktivität zum Indizieren der Quelle verfügt.  
  
3. Fügen Sie der Builddefinition die folgenden MSBuild-Argumente hinzu:  
  
   - **/p:VisualStudioVersion=12.0**  
  
   - **/p:MSBuildAssemblyVersion=12.0**  
  
   - **/tv:12.0**  
  
   - **/p:IncludeServerNameInBuildInfo=True**  
  
   - **/p:BuildSymbolStorePath=** \<*Pfad zu Symbolen*>  
  
4. Führen Sie einen neuen Build aus.  
  
   **Schritt 2:** [Schritt 2: Release your app](#DeployRelease)  
  
### <a name="ManualBuild"></a> Erstellen des Buildmanifests für einen manuellen Buildvorgang mithilfe von Visual Studio  
 Führen Sie die folgenden Schritte aus, um das Buildmanifest (BuildInfo.config) für Ihr Projekt automatisch zu erstellen und in das Ausgabeverzeichnis Ihres Projekts einzufügen. Die Datei erscheint als "*ProjektName*.BuildInfo.config" im Ausgabeverzeichnis, wird jedoch im Bereitstellungsverzeichnis als "BuildInfo.config" umbenannt, nachdem Sie Ihre App veröffentlicht haben.  
  
1. Entladen Sie das Webprojekt im **Projektmappen-Explorer**.  
  
2. Öffnen Sie die Projektdatei (.csproj, .vbproj). Fügen Sie die folgenden Zeilen ein:  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. Checken Sie die aktualisierte Projektdatei ein.  
  
4. Führen Sie einen neuen Build aus.  
  
   **Schritt 2:** [Schritt 2: Release your app](#DeployRelease)  
  
### <a name="MSBuild"></a> Erstellen des Buildmanifests für einen manuellen Buildvorgang mithilfe von „MSBuild.exe“  
 Fügen Sie diese Buildargumente beim Ausführen des Builds hinzu:  
  
 **/p:GenerateBuildInfoConfigFile=True**  
  
 **/p:IncludeServerNameInBuildInfo=True**  
  
 **/p:BuildSymbolStorePath=** \<*Pfad zu Symbolen*>  
  
## <a name="DeployRelease"></a> Schritt 2: Freigeben der App  
 Wenn Sie das [Web.Deploy-Paket](https://msdn.microsoft.com/library/dd394698.aspx) verwenden, das vom Build-Prozess zum Bereitstellen Ihrer App erstellt wurde, wird das Buildmanifest automatisch von „*Projektname*.BuildInfo.config“ zu „BuildInfo.config“ umbenannt und auf dem Webserver im gleichen Verzeichnis wie die Web.config-Datei Ihrer App abgelegt.  
  
 Wenn Sie eine andere Methode zum Bereitstellen Ihrer App verwenden, müssen Sie sicherstellen, dass das Buildmanifest von "*ProjektName*.BuildInfo.config" zu "BuildInfo.config" umbenannt und auf dem Webserver im gleichen Verzeichnis wie die Web.config-Datei Ihrer App abgelegt wird.  
  
## <a name="step-3-monitor-your-app"></a>Schritt 3: Überwachen der App  
 Richten Sie Leistungsüberwachung für Ihre App auf dem Webserver ein, um Ihre App auf Probleme zu untersuchen, Diagnoseereignisse aufzuzeichnen und diese Ereignisse in einer IntelliTrace-Protokolldatei zu speichern. Siehe [Überwachen Ihrer App auf Bereitstellungsprobleme](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="InvestigateEvents"></a> Schritt 4: Ermitteln des Problems  
 Sie benötigen Visual Studio Enterprise auf Ihrem Entwicklungscomputer oder einem anderen Computer, um die aufgezeichneten Ereignisse anzuzeigen und Ihren Code mit IntelliTrace zu debuggen. Sie können alternativ Tools wie CodeLens, IntelliTrace, Debuggerzuordnungen und Codezuordnungen verwenden, um das Problem zu diagnostizieren.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>Öffnen des IntelliTrace-Protokolls und der entsprechenden Projektmappe  
  
1. Öffnen Sie das IntelliTrace-Protokoll (ITRACE-Datei) in Visual Studio Enterprise. Oder doppelklicken Sie einfach auf die Datei, wenn Visual Studio Enterprise auf demselben Computer installiert ist.  
  
2. Wählen Sie **Projektmappe öffnen** aus, damit die entsprechende Projektmappe oder das Projekt automatisch in Visual Studio geöffnet wird, wenn das Projekt nicht als Teil einer Projektmappe erstellt wurde. [Q: The IntelliTrace log is missing information about my deployed app. Why did this happen? What do I do?](#InvalidConfigFile)  
  
     Visual Studio legt alle ausstehenden Änderungen automatisch ab, wenn die entsprechende Projektmappe oder das Projekt geöffnet wird. Nähere Informationen zu diesem Shelvesets finden Sie im Fenster **Ausgabe** oder **Team Explorer**.  
  
     Bevor Sie Änderungen vornehmen, sollten Sie überprüfen, ob Sie über die richtige Quelle verfügen. Wenn Sie Verzweigung verwenden kann es sein, dass die aktuelle Verzweigung von der Verzweigung abweicht, in der Visual Studio die entsprechende Quelle findet, z. B. Ihre Versionsverzweigung.  
  
     ![Open solution from IntelliTrace log](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Wenn Sie einen Arbeitsbereich zu dieser Lösung oder diesem Projekt zugeordnet haben, wählt Visual Studio diesen Arbeitsbereich aus, um die gesuchte Quelle einzufügen.  
  
     ![Open from source control to mapped workspace](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     Andernfalls wählen Sie einen anderen Arbeitsbereich aus oder erstellen Sie einen neuen Arbeitsbereich. Visual Studio ordnet diesem Arbeitsbereich die gesamte Verzweigung zu.  
  
     ![Open from source control &#45; create new workspace](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Um einen Arbeitsbereich mit bestimmten Zuordnungen oder einen Namen zu erstellen, der nicht Ihrem Computernamen entspricht, wählen Sie **Verwalten**aus.  
  
     [F: Warum meldet Visual Studio, dass mein ausgewählter Arbeitsbereich ungültig ist?](#IneligibleWorkspace)  
  
     [F: Warum kann ich den Vorgang erst fortsetzen, wenn ich eine Teamsammlung oder eine andere Sammlung ausgewählt habe?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Diagnose eines Leistungsproblems  
  
1. Unter **Leistungsverletzungen**überprüfen Sie die aufgezeichneten Leistungsereignisse, ihre Gesamtausführungszeiten und andere Ereignisinformationen. Sehen Sie sich anschließend die Details der Methoden näher an, die während eines bestimmten Leistungsereignisses aufgerufen wurden.  
  
     ![View performance event details](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Sie können auch einfach auf das Ereignis doppelklicken.  
  
2. Überprüfen Sie auf der Ereignisseite die Ausführungszeiten für diese Aufrufe. Suchen Sie einen langsamen Aufruf in der Ausführungsstruktur.  
  
     Die langsamsten Aufrufe werden in einem eigenen Bereich angezeigt, wenn Sie mehrere, geschachtelte oder andere Aufrufe haben.  
  
     Erweitern Sie diesen Aufruf, um alle geschachtelten Aufrufe und Werte zu überprüfen, die zu diesem Zeitpunkt aufgezeichnet wurden. Starten Sie dann das Debuggen über diesen Aufruf.  
  
     ![Start debugging from method call](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Sie können auch einfach auf den Aufruf doppelklicken.  
  
     Wenn die Methode in Ihrem Anwendungscode enthalten ist, wechselt Visual Studio zu dieser Methode.  
  
     ![Go to application code from performance event](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Jetzt können Sie andere aufgezeichnete Werte und die Aufrufliste überprüfen, den Code schrittweise durchlaufen oder das Fenster **IntelliTrace** verwenden, um [sich zwischen anderen Methoden zeitlich rückwärts oder vorwärts zu bewegen](../debugger/intellitrace.md) , die während dieses Leistungsereignisses aufgerufen wurden. [Was bedeuten die restlichen Ereignisse und Informationen im IntelliTrace-Protokoll?](../debugger/using-saved-intellitrace-data.md)[What else can I do from here?](#WhatElse)[Wünschen Sie weitere Informationen zu Leistungsereignissen?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)  
  
### <a name="diagnose-an-exception"></a>Diagnose einer Ausnahme  
  
1. Überprüfen Sie unter **Ausnahmedaten**die aufgezeichneten Ausnahmeereignisse, deren Typen und Meldungen und wann die Ausnahmen aufgetreten sind. Um tiefer in den Code zu vorzudringen, starten Sie das Debuggen des letzten Ereignisses in einer Gruppe von Ausnahmen.  
  
     ![Start debugging from exception event](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Sie können auch einfach auf das Ereignis doppelklicken.  
  
     Wenn die Ausnahme im Anwendungscode aufgetreten ist, wechselt Visual Studio zu der Stelle, an der die Ausnahme aufgetreten ist.  
  
     ![Go to application code from an exception event](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Jetzt können Sie andere aufgezeichnete Werte und die Aufrufliste überprüfen oder das Fenster **IntelliTrace** verwenden, um [sich zwischen anderen aufgezeichneten Ereignissen](../debugger/intellitrace.md), zugehörigem Code und den Werten zu bewegen, die zu diesen Zeitpunkten erfasst wurden. [Was bedeuten die restlichen Ereignisse und Informationen im IntelliTrace-Protokoll?](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="WhatElse"></a> Welche weiteren Möglichkeiten gibt es hier?  
  
- [Rufen Sie mehr Informationen zu diesem Code ab](../ide/find-code-changes-and-other-history-with-codelens.md). Um Verweise für diesen Code, dessen Änderungsverlauf und alle entsprechenden Fehler, Arbeitselemente, Codeüberprüfungsanforderungen oder Komponententests zu suchen, ohne den Editor zu verlassen, können Sie die CodeLens-Indikatoren im Editor verwenden.  
  
     ![CodeLens &#45; View references to this code](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; View change history for this code](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
- [Ordnen Sie die Stelle im Code während des Debuggens zu.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Um die Methoden, die während der Debugsitzung aufgerufen wurden, visuell nachzuverfolgen, ordnen Sie die Aufrufliste zu.  
  
     ![Map the call stack while debugging](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
### <a name="FAQ"></a> Fragen und Antworten  
  
#### <a name="WhyInclude"></a> F: Warum sollte ich Informationen über mein Projekt, die Quellcodeverwaltung, Version und Symbole in meine Version aufnehmen?  
 Visual Studio verwendet diese Informationen, um die passende Lösung und den entsprechenden Quellcode für die Version zu finden, die Sie gerade debuggen. Nachdem Sie das IntelliTrace-Protokoll geöffnet und ein zu debuggendes Ereignis ausgewählt haben, zeigt Ihnen Visual Studio anhand der Symbole den Code, in dem das Ereignis aufgetreten ist. Anschließend können Sie die aufgezeichneten Werte anzeigen und den ausgeführten Code vorwärts und rückwärts durchlaufen.  
  
 Falls Sie TFS verwenden und Ihr Buildmanifest (Datei BuildInfo.config) diese Informationen nicht enthält, sucht Visual Studio in Ihrem aktuell verbundenen TFS nach dem passenden Quellcode und den entsprechenden Symbolen. Wenn Visual Studio das korrekte TFS oder den entsprechenden Quellcode nicht findet, werden Sie aufgefordert, ein anderes TFS auszuwählen.  
  
#### <a name="InvalidConfigFile"></a> F: Im IntelliTrace-Protokoll fehlen Informationen über die bereitgestellte App. Wie konnte das geschehen? Was kann ich unternehmen?  
 Dies kann geschehen, wenn Sie die App von Ihrem Entwicklungscomputer bereitstellen oder bei der Bereitstellung nicht mit dem TFS verbunden sind.  
  
1. Öffnen Sie den Bereitstellungsordner Ihres Projekts.  
  
2. Suchen und öffnen Sie das Buildmanifest (BuildInfo.config-Datei).  
  
3. Vergewissern Sie sich, dass die folgenden Informationen enthalten sind:  
  
- **ProjectName**  
  
   Der Name Ihres Projekts in Visual Studio. Beispiel:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Informationen über Ihr Quellcodeverwaltungssystem und die folgenden erforderlichen Eigenschaften:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: der URI für Ihren Team Foundation Server und Ihre Projektsammlung  
  
    - **ProjectItemSpec**: der Pfad zur Projektdatei Ihrer App (.csproj oder .vbproj)  
  
    - **ProjectVersionSpec**: die Version Ihres Projekts  
  
      Beispiel:  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Git**  
  
    - **GitSourceControl**: der Speicherort des **GitSourceControl** -Schemas  
  
    - **RepositoryUrl**: der URI für Ihren Team Foundation Server, Ihre Projektsammlung und Ihr Git-Repository  
  
    - **ProjectPath**: der Pfad zur Projektdatei Ihrer App (.csproj oder .vbproj)  
  
    - **CommitId**: die ID Ihres Commits  
  
      Beispiel:  
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- **Erstellen**  
  
   Informationen über Ihr Buildsystem, entweder `"TeamBuild"` oder `"MSBuild"`, sowie die folgenden erforderlichen Eigenschaften:  
  
  - **BuildLabel** (für TeamBuild): Buildname und -Nummer. Diese Bezeichnung wird auch als Name des Bereitstellungsereignisses verwendet. Weitere Informationen zu Buildnummern finden Sie unter [Verwenden von Buildnummern, um abgeschlossene Builds mit aussagekräftigen Namen zu versehen](https://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath** (empfohlen): die Liste der URIs für die Orte Ihrer Symbole (PDB-Datei) getrennt durch Semikolons. Diese URIs können URLs oder Netzwerkpfade (UNC) sein. Dies erleichtert Visual Studio das Auffinden der entsprechenden Symbole zum Debuggen.  
  
  - **BuildReportUrl** (für TeamBuild): Buildberichtsspeicherort in TFS  
  
  - **BuildId** (für TeamBuild): URI für die Builddetails in TFS. Dieser URI wird auch als ID des Bereitstellungsereignisses verwendet. Diese ID muss eindeutig sein, wenn Sie TeamBuild nicht verwenden.  
  
  - **BuiltSolution**: der Pfad zur Projektmappendatei, die Visual Studio zum Suchen und Öffnen der entsprechenden Projektmappe verwendet. Dies ist der Inhalt der MsBuild-Eigenschaft **SolutionPath** .  
  
    Beispiel:  
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
#### <a name="IneligibleWorkspace"></a> F: Warum meldet Visual Studio, dass mein ausgewählter Arbeitsbereich ungültig ist?  
 **A:** Der ausgewählte Arbeitsbereich besitzt keine Zuordnungen zwischen dem Quellverwaltungsordner und einem lokalen Ordner. Um eine Zuordnung für diesen Arbeitsbereich zu erstellen, wählen Sie **Verwalten**aus. Andernfalls wählen Sie einen bereits zugeordneten Arbeitsbereich aus oder erstellen Sie einen neuen Arbeitsbereich.  
  
 ![Open from source control with no mapped workspace](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
#### <a name="ChooseTeamProject"></a> F: Warum kann ich den Vorgang erst fortsetzen, wenn ich eine Teamsammlung oder eine andere Sammlung ausgewählt habe?  
 **A:** Dies kann aus folgenden Gründen der Fall sein:  
  
- Visual Studio ist nicht mit dem TFS verbunden.  
  
     ![Open from source control &#45; not connected](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
- Visual Studio konnte die Projektmappe oder das Projekt nicht in der aktuellen Teamauflistung finden.  
  
     Wenn die Buildmanifestdatei (\<*ProjektName*>.BuildInfo.config) nicht angibt, wo Visual Studio die entsprechende Quelle finden kann, verwendet Visual Studio den aktuell verbundenen TFS, um die entsprechende Projektmappe oder das Projekt zu suchen. Wenn die aktuelle Teamauflistung nicht über die entsprechende Quelle verfügt, fordert Visual Studio Sie auf, eine Verbindung mit einer anderen Teamauflistung herzustellen.  
  
- Visual Studio konnte die Projektmappe oder das Projekt nicht in der von der Buildmanifestdatei (\<*ProjektName*>.BuildInfo.config) angegeben Sammlung finden.  
  
     Der angegebene TFS verfügt möglicherweise nicht mehr über die entsprechende Quelle oder Sie ist nicht mehr vorhanden, da Sie möglicherweise zu einem neuen TFS migriert sind. Wenn der angegebene TFS nicht vorhanden ist, kann bei Visual Studio nach etwa einer Minute ein Timeout auftreten, und Sie werden anschließend aufgefordert, eine Verbindung mit einer anderen Auflistung herzustellen. Um den Vorgang fortzusetzen, stellen Sie eine Verbindung mit dem richtigen TFS her.  
  
     ![Open from source control &#45; migrated](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
#### <a name="WhatWorkspace"></a> F: Was ist ein Arbeitsbereich?  
 **A:** Der [Arbeitsbereich speichert eine Kopie der Quelle](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) sodass Sie sie separat entwickeln und testen können, bevor Sie die Arbeit einchecken. Wenn Sie nicht bereits über einen Arbeitsbereich verfügen, der der gefundenen Projektmappe oder dem Projekt speziell zugeordnet ist, dann werden Sie von Visual Studio aufgefordert, einen verfügbaren Arbeitsbereich auszuwählen oder einen neuen Arbeitsbereich mit Ihrem Computernamen als Standardarbeitsbereichsname zu erstellen.  
  
#### <a name="UntrustedSymbols"></a> F: Warum erhalte ich diese Meldung über nicht vertrauenswürdige Symbole?  
 ![Debug with untrusted symbols path?](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **A:** Diese Meldung wird angezeigt, wenn der Symbolpfad in der Buildmanifestdatei (\<*ProjectName*>.BuildInfo.config) nicht in der Liste der vertrauenswürdigen Symbolpfade enthalten ist. Sie können den Pfad zur Liste der Symbolpfade in den Debuggeroptionen hinzufügen.
