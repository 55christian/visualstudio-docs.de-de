---
title: Debuggen von SharePoint-Anwendung mit IntelliTrace
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59407696743b15262db83f915feb075a10e22225
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401045"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mit IntelliTrace

Mit IntelliTrace können Sie SharePoint-Lösungen einfacher debuggen. Herkömmliche Debugger erstellen lediglich eine aktuelle Momentaufnahme der Lösung. Sie können mithilfe von IntelliTrace jedoch in der Lösung aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind, überprüfen und zum Code navigieren.

 Diese exemplarische Vorgehensweise veranschaulicht, wie Sie eine SharePoint 2010 oder SharePoint 2013-Projekt in Visual Studio zu debuggen, indem Sie mit Microsoft Monitoring Agent zum Sammeln von IntelliTrace-Daten bereitgestellter Anwendungen. Um diese Daten zu analysieren, müssen Sie Visual Studio Enterprise verwenden. Dieses Projekt integriert einen Funktionsempfänger, der bei aktivierter Funktion der Liste „Aufgaben“ eine Aufgabe und der Liste „Ankündigungen“ eine Ankündigung hinzufügt. Wenn die Funktion deaktiviert wird, wird die Aufgabe als abgeschlossen gekennzeichnet, und der Liste "Ankündigungen" wird eine zweite Ankündigung hinzugefügt. Die Prozedur enthält jedoch einen logischen Fehler, der verhindert, dass das Projekt ordnungsgemäß ausgeführt wird. Mit IntelliTrace können Sie den Fehler suchen und korrigieren.

 **Gilt für:** Die Informationen in diesem Thema gelten für SharePoint 2010 und SharePoint 2013-Lösungen, die in Visual Studio erstellt wurden.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- [Einen Funktionsempfänger erstellen](#create-a-feature-receiver)

- [Fügen Sie dem Funktionsempfänger Code hinzu](#add-code-to-the-feature-receiver)

- [Testen Sie das Projekt](#test-the-project)

- [Sammeln von IntelliTrace-Daten mithilfe von Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Debuggen Sie und korrigieren Sie die SharePoint-Lösung](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Windows und SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Einen Funktionsempfänger erstellen

Erstellen Sie zunächst ein leeres SharePoint-Projekt mit einem Funktionsempfänger.

1. Erstellen Sie ein Projekt für SharePoint 2010 oder SharePoint 2013-Lösung, und nennen Sie es **IntelliTraceTest**.

     Die **SharePoint Customization Wizard** angezeigt wird, in dem Sie die SharePoint-Website für Ihr Projekt und die Vertrauensebene der Projektmappe angeben können.

2. Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     IntelliTrace kann nur für Farmlösungen verwendet werden.

3. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Features** Knoten, und wählen Sie dann **Feature hinzufügen**.

     *"Feature1.Feature"* angezeigt wird.

4. Öffnen Sie das Kontextmenü für "Feature1.Feature", und wählen Sie dann **Ereignisempfänger hinzufügen** ein Codemodul mit dem Feature hinzufügen.

## <a name="add-code-to-the-feature-receiver"></a>Fügen Sie dem Funktionsempfänger Code hinzu

Fügen Sie anschließend zwei Methoden im Funktionsempfänger Code hinzu: `FeatureActivated` und `FeatureDeactivating`. Diese Methoden lösen immer dann aus, wenn eine Funktion in SharePoint aktiviert bzw. deaktiviert wird.

1. Fügen Sie am Anfang der `Feature1EventReceiver`-Klasse den folgenden Code hinzu, um Variablen zu deklarieren, mit denen die SharePoint-Website und -Unterwebsite angegeben werden:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Ersetzen Sie die `FeatureActivated`-Methode durch folgenden Code:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Ersetzen Sie die `FeatureDeactivating`-Methode durch folgenden Code:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Testen Sie das Projekt

Wenn dem Funktionsempfänger der Code hinzugefügt wurde und der Datensammler ausgeführt wird, stellen Sie die SharePoint-Lösung bereit. Führen Sie sie aus, um die ordnungsgemäße Funktion zu testen.

> [!IMPORTANT]
> In diesem Beispiel wird ein Fehler im Ereignishandler „FeatureDeactivating“ ausgelöst. Im weiteren Verlauf dieser exemplarischen Vorgehensweise suchen Sie diesen Fehler anhand der vom Datensammler erstellten .iTrace-Datei.

1. Stellen Sie die Lösung für SharePoint bereit, und öffnen Sie die SharePoint-Website in einem Browser.

     Die Funktion wird automatisch aktiviert. Dadurch wird bewirkt, dass der Funktionsempfänger eine Ankündigung und eine Aufgabe hinzufügt.

2. Zeigen Sie den Inhalt der Listen mit Ankündigungen und Aufgaben an.

     Die Liste der Ankündigungen müssen eine neue Ankündigung mit dem Namen **Activated Feature: IntelliTraceTest_Feature1**, und die Aufgabenliste sollte eine neue Aufgabe mit dem Namen **Deactivate Feature: IntelliTraceTest_Feature1**. Wenn eines der Elemente fehlt, überprüfen Sie, ob die Funktion aktiviert ist. Aktivieren Sie sie andernfalls.

3. Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:

   1. Auf der **Websiteaktionen** Menü in SharePoint **Standorteinstellungen**.

   2. Klicken Sie unter **Websiteaktionen**, wählen Sie die **Websitefeatures verwalten** Link.

   3. Neben **IntelliTraceTest Feature1**, wählen Sie die **deaktivieren** Schaltfläche.

   4. Wählen Sie auf der Seite Warnung die **deaktivieren Sie dieses Feature** Link.

      Vom Ereignishandler „FeatureDeactivating()“ wird ein Fehler ausgelöst.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Sammeln von IntelliTrace-Daten mithilfe von Microsoft Monitoring Agent

Wenn Sie Microsoft Monitoring Agent auf dem System, auf dem SharePoint ausgeführt wird installieren, können Sie die SharePoint-Lösungen Debuggen, mit Daten, die präziser als die allgemeine Informationen, die von IntelliTrace zurückgegeben. Der Agent funktioniert außerhalb von Visual Studio, indem PowerShell-Cmdlets verwendet werden, um Debuginformationen zu sammeln, während die SharePoint-Lösung ausgeführt wird.

> [!NOTE]
> Die Konfigurationsinformationen in diesem Abschnitt beziehen sich auf dieses Beispiel. Weitere Informationen über andere Konfigurationsoptionen finden Sie unter [mit den eigenständigen IntelliTrace Collector](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Auf dem Computer, auf dem SharePoint ausgeführt wird [Microsoft Monitoring Agent installieren und starten Sie zum Überwachen Ihrer Lösung](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Deaktivieren Sie die Funktion:

   1. Auf der **Websiteaktionen** Menü in SharePoint **Standorteinstellungen**.

   2. Klicken Sie unter **Websiteaktionen**, wählen Sie die **Websitefeatures verwalten** Link.

   3. Neben **IntelliTraceTest Feature1**, wählen Sie die **deaktivieren** Schaltfläche.

   4. Wählen Sie auf der Seite Warnung die **deaktivieren Sie dieses Feature** Link.

      Ein Fehler tritt auf (in diesem Fall aufgrund des Fehlers im Ereignishandler "FeatureDeactivating()").

3. Führen Sie im PowerShell-Fenster, das [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) Befehl aus, um die ITRACE-Datei erstellen, Überwachung zu beenden und starten Sie die SharePoint-Lösung neu.

     **Stop-WebApplicationMonitoring** *"\<SharePointSite >\\< SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>Debuggen Sie und korrigieren Sie die SharePoint-Lösung

Jetzt können Sie die IntelliTrace-Protokolldatei in Visual Studio anzeigen, um den Fehler in der SharePoint-Lösung zu suchen und zu beheben.

1. Öffnen Sie im Ordner "\IntelliTraceLogs" die ITRACE-Datei-Datei in Visual Studio.

     Die **IntelliTrace-Zusammenfassung** Seite wird angezeigt. Da der Fehler nicht behandelt wurde, eine SharePoint-Korrelations-ID (eine GUID) wird angezeigt, im Bereich nicht behandelte Ausnahme die **Analysis** Abschnitt. Wählen Sie die **Aufrufliste** Schaltfläche sollten Sie die Aufrufliste anzuzeigen, in dem der Fehler aufgetreten ist.

2. Wählen Sie die **Debugausnahme** Schaltfläche.

     Wenn Sie dazu aufgefordert werden, laden Sie Symboldateien. In der **IntelliTrace** Fenster die Ausnahme wird hervorgehoben, wenn "ausgelöst: Schwerwiegender Fehler aufgetreten! ".

     Wählen Sie die Ausnahme im IntelliTrace-Fenster aus, um den Code mit dem Fehler anzuzeigen.

3. Die Fehler beheben, indem Sie die SharePoint-Projektmappe öffnen, und klicken Sie dann entweder auskommentieren oder Entfernen der **auslösen** -Anweisung am Anfang der Prozedur FeatureDeactivating().

4. Erstellen Sie die Projektmappe in Visual Studio neu, und stellen Sie sie dann erneut für SharePoint bereit.

5. Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:

    1. Auf der **Websiteaktionen** Menü in SharePoint **Standorteinstellungen**.

    2. Klicken Sie unter **Websiteaktionen**, wählen Sie die **Websitefeatures verwalten** Link.

    3. Neben **IntelliTraceTest Feature1**, wählen Sie die **deaktivieren** Schaltfläche.

    4. Wählen Sie auf der Seite Warnung die **deaktivieren Sie dieses Feature** Link.

6. Öffnen Sie die Aufgabenliste, und überprüfen Sie, ob die **Status** Wert des Tasks "deaktivieren" "abgeschlossen" und die zugehörige **% abgeschlossen** Wert beträgt 100 %.

     Der Code wird jetzt ordnungsgemäß ausgeführt.

## <a name="see-also"></a>Siehe auch

- [Überprüfen und Debuggen von SharePoint-code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Exemplarische Vorgehensweise: Überprüfen Sie die SharePoint-Code mit Komponententests](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))