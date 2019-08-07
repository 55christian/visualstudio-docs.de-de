---
title: Bearbeiten von Abonnements im Verwaltungsportal | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Abonnementzuweisungen bearbeiten können.
ms.openlocfilehash: e55cee74f861973e3cc29e3f19dc9b31a107f437
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605661"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Bearbeiten von Visual Studio-Abonnementzuweisungen
Als Abonnementadministrator können Sie Änderungen an den Abonnements vornehmen, die Personen innerhalb Ihrer Organisation zugewiesen sind.  Dieser Artikel beschreibt die Arten von Änderungen, die Sie vornehmen können, und enthält die notwendigen Schritte.

## <a name="change-subscriber-information"></a>Eingeben der Abonnenteninformationen
Sie können die Informationen eines Abonnenten bearbeiten, um Fehler zu beheben und Informationen zu aktualisieren.

Klicken Sie für das Bearbeiten eines Abonnenten auf die Auslassungspunkte (...), die neben der E-Mail-Adresse des Abonnenten angezeigt werden, wenn Sie mit der Maus darauf zeigen. Eine Dropdownliste wird angezeigt.  Klicken Sie auf **Bearbeiten**, um die Details des Abonnenten zu ändern. Sie können ebenfalls auf die Zeile des Abonnenten im Raster doppelklicken, um das Bearbeitungsfenster zu öffnen.
> [!div class="mx-imgBorder"]
> ![Auswählen des zu bearbeitenden Abonnenten](_img/edit-license/select-subscriber.png)

Sie können den Vornamen, den Nachnamen, das Land, die Sprache und die Downloads des Abonnenten aktualisieren. Bearbeiten Sie die Informationen des Abonnenten, und klicken Sie dann auf **Speichern**.

   > [!NOTE]
   > Wenn Sie die Abonnementebene für einen Abonnenten ändern müssen, müssen Sie den Benutzer aus dem Portal löschen und erneut hinzufügen. Abonnementebenen können nicht bearbeitet werden.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung
Sie können mehrere Abonnenten gleichzeitig bearbeiten, wenn Sie die Massenbearbeitung verwenden. Diese Funktion wird in erster Linie für Organisationen verwendet, wenn die geschäftlichen E-Mail-Adressen geändert werden, oder wenn eine Organisation sich dafür entschieden hat, den Zugriff auf Downloads zu beschränken.

   > [!IMPORTANT]
   > Abonnementebenen (d.h. Enterprise, Professional usw.) und Abonnement-GUIDs können nicht geändert werden.  Wenn Sie etwas hochladen möchten und diese Elemente verändert wurden, schlägt der Upload fehl.

1. Navigieren Sie zur Registerkarte „Abonnenten“, um mehrere Abonnenten gleichzeitig zu bearbeiten. Klicken Sie im oberen Bereich des Menübands auf **Massenbearbeitung**.

2. Die Massenbearbeitung verwendet eine Excel-Vorlage, um Änderungen an Abonnenteninformationen vorzunehmen. Klicken Sie im Feld „Massenbearbeitung“ auf **Export this Excel** (Diese Excel-Datei exportieren), um die aktuelle Liste der Abonnenten einschließlich aller Informationen herunterzuladen.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Exportieren der Massenbearbeitungsliste](_img/edit-license/edit-license-bulk-edit-export.png)

3. Speichern Sie die Datei lokal, damit Sie diese einfach finden und vor dem Upload erforderliche Änderungen vornehmen können. Für einen erfolgreichen Upload sollten Sie **die Abonnementebene oder Abonnement-GUID nicht bearbeiten**, da dies dazu führt, dass der Upload fehlschlägt.

4. Wechseln Sie zum Administratorportal für Visual Studio-Abonnements, und klicken Sie im Dialogfeld „Massenbearbeitung“ auf **Durchsuchen**. Wählen Sie die Excel-Datei aus, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt.
   > [!div class="mx-imgBorder"]
   > ![Bearbeiten einer Lizenz: Massenbearbeitungen – Dateiupload](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Sobald Sie die Datei hochgeladen haben, wird Ihnen eine Benachrichtigung angezeigt, dass der Upload erfolgreich war. Jetzt sind Ihre Änderungen in den Abonnenteninformationen zu enthalten.

## <a name="next-steps"></a>Nächste Schritte
- Um ein bestimmtes Abonnement zu finden, informieren Sie sich unter [Suchen nach einem Abonnement](search-license.md).
- Müssen Sie eine Liste all Ihrer Abonnements erstellen?  Informieren Sie sich unter [Exportieren von Abonnements](exporting-subscriptions.md).