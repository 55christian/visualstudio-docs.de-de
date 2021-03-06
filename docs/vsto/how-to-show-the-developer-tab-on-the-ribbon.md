---
title: 'Vorgehensweise: Anzeigen der Registerkarte "Entwickler" im Menüband'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551788"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Vorgehensweise: Anzeigen der Registerkarte "Entwickler" im Menüband
  Wenn Sie auf dem Menüband einer Office-Anwendung auf die Registerkarte **Entwickler** zugreifen möchten, müssen Sie Sie so konfigurieren, dass diese Registerkarte angezeigt wird, da Sie standardmäßig nicht angezeigt wird Beispielsweise müssen Sie diese Registerkarte anzeigen, wenn Sie <xref:Microsoft.Office.Tools.Word.GroupContentControl> einer Anpassung auf Dokumentebene für Word hinzufügen möchten.

> [!NOTE]
> Dieser Leitfaden gilt nur für Office 2010-Anwendungen und neuer. Wenn Sie diese Registerkarte im 2007-Microsoft Office System anzeigen möchten, lesen Sie die folgende Version dieses Themas [: Anzeigen der Registerkarte "Entwickler"](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)im Menüband.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Der Zugriff hat keine Registerkarte " **Entwickler** ".

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Anzeigen der Registerkarte "Entwickler"

1. Starten Sie eine der Office-Anwendungen, die in diesem Thema beschrieben werden. Weitere Informationen finden Sie weiter oben in diesem Thema unter **betrifft:** Hinweis.

2. Wählen Sie auf der Registerkarte **Datei** die Schaltfläche **Optionen** aus.

     Die folgende Abbildung zeigt die Registerkarte **Datei** und die Schaltfläche **Optionen** in Office 2010.

     ![Auswählen von "Datei", "Optionen" in Outlook 2010](../vsto/media/vsto-office-file-tab.png "Auswählen von \"Datei\", \"Optionen\" in Outlook 2010")

     In der folgenden Abbildung wird die Registerkarte **Datei** in Office 2013 angezeigt.

     ![Registerkarte "Datei" in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Registerkarte \"Datei\" in Outlook 2013")

     In der folgenden Abbildung wird die Schaltfläche **Optionen** in Office 2013 angezeigt.

     ![Schaltfläche "Optionen" in Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Schaltfläche \"Optionen\" in Outlook 2013 Preview")

3. Wählen Sie im Dialogfeld _ApplicationName_-**Optionen** die Schaltfläche **Menüband anpassen** aus.

     Die folgende Abbildung zeigt das Dialogfeld **Optionen** und die Schaltfläche **Menüband anpassen** in Excel 2010. Der Speicherort dieser Schaltfläche ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.

     ![Schaltfläche "Menüband anpassen] " (../vsto/media/vsto-office2010-customizeribbonbutton.png "Schaltfläche \"Menüband anpassen") "

4. Aktivieren Sie in der Liste der Haupt Registerkarten das Kontrollkästchen **Entwickler** .

     In der folgenden Abbildung wird das Kontrollkästchen für **Entwickler** in Word [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]2010 und angezeigt. Der Speicherort dieses Kontrollkästchens ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.

     ![Das Kontrollkästchen "Entwickler" im Dialogfeld "Word-Optionen] " (../vsto/media/vsto-office2010-developercheckbox.png "Das Kontrollkästchen \"Entwickler\" im Dialogfeld \"Word-Optionen") "

5. Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld **Optionen** zu schließen.

## <a name="see-also"></a>Siehe auch
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
