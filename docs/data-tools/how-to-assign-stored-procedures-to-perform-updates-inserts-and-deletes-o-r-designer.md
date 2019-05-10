---
title: Verwenden Sie gespeicherte Prozeduren zum Ausführen von Update-, insert und delete in Linq to SQL-O/R-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da666f237824ccae349a023611f7e7b78fdaf684
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402831"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)

Gespeicherte Prozeduren können dem **O/R-Designer** hinzugefügt und als typische <xref:System.Data.Linq.DataContext>-Methoden ausgeführt werden. Sie können auch verwendet, das standardmäßige LINQ to SQL-Laufzeitverhalten zu überschreiben, die Einfüge-, Update- und Löschvorgänge ausführt, wenn Änderungen von Entitätsklassen in einer Datenbank gespeichert werden (z. B. beim Aufrufen der <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Methode).

> [!NOTE]
> Wenn Ihre gespeicherte Prozedur Werte zurückgibt, die an den Client zurückgesendet werden müssen (beispielsweise Werte, die in der gespeicherten Prozedur berechnet werden), sollten Sie Ausgabeparameter in Ihrer gespeicherten Prozedur erstellen. Wenn Sie keine Ausgabeparameter verwenden können, sollten Sie eine partielle Methodenimplementierung schreiben und sich nicht auf vom O/R-Designer erzeugte Überschreibungen verlassen. Member, die datenbankgenerierten Werten zugeordnet werden, müssen nach erfolgreicher Beendigung von INSERT- oder UPDATE-Vorgängen auf entsprechende Werte festgelegt werden. Weitere Informationen finden Sie unter [Verantwortlichkeiten der Entwickler In Überschreiben von Standardverhalten](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL behandelt datenbankgenerierte Werte für die Identität (automatisch inkrementierten), ROWGUID-(datenbankgenerierte GUID) und Timestamp-Spalten automatisch. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Sie sollten manuell festlegen, um die datenbankgenerierten Werte zurückzugeben, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> zu **"true"** und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf einen der folgenden: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), oder [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurieren des Updateverhaltens einer Entitätsklasse

Standardmäßig wird die Logik, mit eine Datenbank (einfügungen, Updates und löschungen) mit Änderungen zu aktualisieren, die auf die Daten in LINQ to SQL-Entitätsklassen vorgenommen wurden von der LINQ to SQL-Laufzeit bereitgestellt. Basierend auf dem Schema der Tabelle (den Spalten- und Primärschlüsselinformationen) werden von der Laufzeit Standardbefehle für INSERT, UPDATE und DELETE erstellt. Wenn das Standardverhalten nicht erwünscht ist, kann das Updateverhalten konfiguriert werden, indem spezielle gespeicherte Prozeduren zur Durchführung der erforderlichen Einfüge-, Update- und Löschvorgänge für die Bearbeitung der Daten in der Tabelle zugewiesen werden. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Schließlich kann das standardmäßige Updateverhalten auch dann überschrieben werden, wenn die Datenbank den Zugriff auf Tabellen über gespeicherte Prozeduren erfordert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>So weisen Sie gespeicherte Prozeduren zu, um das Standardverhalten einer Entitätsklasse zu überschreiben

1. Öffnen Sie die **LINQ to SQL**-Datei im Designer. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)

2. Erweitern Sie im **Server-Explorer** oder **Datenbank-Explorer** den Knoten **Gespeicherte Prozeduren**, und suchen Sie die gespeicherten Prozeduren, die für die Einfüge-, Update- und/oder Löschbefehle der Entitätsklasse verwendet werden sollen.

3. Ziehen Sie die gespeicherte Prozedur in den **O/R-Designer**.

     Die gespeicherte Prozedur wird dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methode hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wählen Sie die Entitätsklasse aus, für die die gespeicherte Prozedur zur Durchführung von Updates verwendet werden soll.

5. Wählen Sie im Fenster **Eigenschaften** den Befehl aus, der überschrieben werden soll (**Einfügen**, **Aktualisieren** oder **Löschen**).

6. Klicken Sie auf die Auslassungszeichen (...) neben den Wörtern **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.

7. Wählen Sie **Anpassen** aus.

8. Wählen Sie die gewünschte gespeicherte Prozedur in der Liste **Anpassen** aus.

9. Untersuchen Sie die Listen **Methodenargumente** und **Klasseneigenschaften**, um zu überprüfen, ob die **Methodenargumente** den entsprechenden **Klasseneigenschaften** zugeordnet sind. Ordnen Sie die ursprünglichen Methodenargumente (`Original_<ArgumentName>`) den ursprünglichen Eigenschaften (`<PropertyName> (Original)`) für die `Update` und `Delete` Befehle.

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn geänderte Eigenschaftennamen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es notwendig sein, die entsprechende Klasseneigenschaft für die Zuordnung auszuwählen, wenn der Designer die korrekte Zuordnung nicht ermitteln kann.

10. Klicken Sie auf **OK** oder auf **Anwenden**.

    > [!NOTE]
    > Sie können das Verhalten für jede Kombination aus Klasse und Verhalten zu konfigurieren, solange Sie klicken Sie auf Weiter **übernehmen** nach jeder Änderung. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf **übernehmen**, ein Warndialogfeld angezeigt wird, und bietet Ihnen die Möglichkeit, die Änderungen zu übernehmen.

Um zur Verwendung der Standardlaufzeitlogik für Updates zurückzukehren, klicken Sie im Fenster **Eigenschaften** auf die Auslassungszeichen neben dem **Einfüge-**, **Update-** oder **Löschbefehl**, und wählen Sie dann im Dialogfeld **Verhalten konfigurieren** die Option **Laufzeit verwenden** aus.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Einfügen, aktualisieren und delete-Operationen ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)