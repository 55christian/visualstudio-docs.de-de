---
title: Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)
ms.date: 02/12/2019
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d4fcce4664483cd1d981f6a0b1233a6302c553b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568541"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)

Sie können mit einer Access-Datenbank verbinden (entweder ein *mdf* Datei oder ein *ACCDB* Datei) mithilfe von Visual Studio. Nachdem Sie die Verbindung definiert haben, werden die Daten im Fenster **Datenquellen** angezeigt. Von dort können Sie Tabellen oder Ansichten auf die Formulare ziehen.

## <a name="prerequisites"></a>Vorraussetzungen

Zum Verwenden dieser Prozeduren benötigen Sie ein Windows Forms-Anwendungsprojekt und entweder eine Access-Datenbank (*ACCDB*-Datei) oder eine Datenbank unter Access 2000–2003 (*MDB*-Datei). Führen Sie die Prozedur aus, die dem Dateityp entspricht.

## <a name="create-a-dataset-for-an-accdb-file"></a>Erstellen eines Datasets für eine ACCDB-Datei

Sie können mit Datenbanken über Access 2013, Office 365, Access 2010 oder Access 2007 erstellt wurden, mithilfe des folgenden Verfahrens verbinden.

1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.

2. Zum Öffnen der **Datenquellen** Fenster auf der **Ansicht** , wählen Sie im Menü **andere Windows** > **Datenquellen**.

   ![Weitere Windows-Datenquellen anzeigen](../data-tools/media/viewdatasources.png)

3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

   Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

4. Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.

5. Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.

6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.

   Das Dialogfeld **Verbindung hinzufügen** wird geöffnet.

7. Wenn **Datenquelle** ist nicht festgelegt, um **Microsoft Access-Datenbankdatei (OLE DB)**, wählen die **Änderung** Schaltfläche.

   Die **Datenquelle wechseln** Dialogfeld wird geöffnet. Wählen Sie in der Liste der Datenquellen, **Microsoft Access-Datenbankdatei**. In der **Datenanbieter** Dropdown-Menü, Option **.NET Framework-Datenanbieter für OLE DB**, und wählen Sie dann **OK**.

8. Wählen Sie **Durchsuchen** neben **Name der Datenbankdatei**, und navigieren Sie zu Ihrem *ACCDB* Datei, und wählen **öffnen**.

9. Geben Sie einen Benutzernamen und Kennwort (falls erforderlich), und wählen Sie dann **OK**.

10. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.

     Sie erhalten möglicherweise ein Dialogfeld angezeigt, die die Datendatei nicht im aktuellen Projekt vorhanden ist. Wählen Sie **Ja** oder **Nein**.

11. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.

12. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

13. Wählen Sie die Tabellen oder Sichten, die Sie verwenden möchten, im Dataset, und wählen Sie dann **Fertig stellen**.

     Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.

## <a name="create-a-dataset-for-an-mdb-file"></a>Erstellen eines Datasets für eine MDB-Datei

Das Dataset wird erstellt, indem der **Assistent zum Konfigurieren von Datenquellen** ausgeführt wird.

1. Öffnen Sie die Windows Forms-Anwendung, mit der Sie Daten verknüpfen möchten.

2. Auf der **Ansicht** , wählen Sie im Menü **Other Windows** > **Datenquellen**.

   ![Weitere Windows-Datenquellen anzeigen](../data-tools/media/viewdatasources.png)

3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

    Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

4. Wählen Sie **Datenbank** auf die **wählen Sie einen Datenquellentyp** Seite, und wählen Sie dann **Weiter**.

5. Wählen Sie **Dataset** auf die **Auswählen eines Datenbankmodells** Seite, und wählen Sie dann **Weiter**.

6. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** die Option **Neue Verbindung** aus, um eine neue Datenverbindung zu konfigurieren.

7. Die Datenquelle ist nicht **Microsoft Access-Datenbankdatei (OLE DB)** wählen **Änderung** zu öffnen der **Datenquelle wechseln** , und wählen Sie im Dialogfeld **Microsoft Zugriff auf die Datenbankdatei**, und wählen Sie dann **OK**.

8. In der **Name der Datenbankdatei**, geben Sie den Pfad und Namen von der *MDB* Datei, die Sie verwenden möchten, Herstellen einer Verbindung mit, und wählen Sie dann **OK**.

   ![Verbindungszugriff-Datenbankdatei hinzufügen](../data-tools/media/add-connection-access-db.png)

9. Wählen Sie **Weiter** auf die **wählen Sie Ihre Datenverbindung** Seite.

10. Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** Seite.

11. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

12. Wählen Sie alle Tabellen oder Sichten, die im Dataset werden soll, und wählen Sie dann **Fertig stellen**.

    Das DataSet wird Ihrem Projekt hinzugefügt, und die Tabellen und Ansichten werden im Fenster **Datenquellen** angezeigt.

## <a name="security"></a>Sicherheit

Das Speichern vertraulicher Informationen (z. B. ein Kennwort) kann sich auf die Sicherheit der Anwendung auswirken. Der Zugriff auf eine Datenbank lässt sich mithilfe der Windows-Authentifizierung (wird auch als integrierte Sicherheit bezeichnet) sicherer steuern. Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Nächste Schritte

Das Dataset, das Sie gerade erstellt haben, ist jetzt verfügbar ist, in der **Datenquellen** Fenster. Sie können nun eine der folgenden Aufgaben ausführen:

- Wählen Sie Elemente in der **Datenquellen** Fenster und ziehen Sie sie auf das Formular (finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Öffnen Sie die Datenquelle im **DataSet-Designer**, um die Objekte, aus denen das Dataset besteht, zu bearbeiten oder dem Dataset Objekte hinzuzufügen.

- Eine Validierungslogik Hinzufügen der <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignis der Datentabellen im Dataset (finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Verbindungen](../data-tools/add-new-connections.md)