---
title: Besondere sicherheitsüberlegungen für Office-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a29c813a5217e68541fd076eadf62bf54710014
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436488"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Besondere sicherheitsüberlegungen für Office-Projektmappen
  Die von Microsoft .NET Framework und Microsoft Office bereitgestellten Sicherheitsfeatures können in Office-Projektmappen zum Schutz vor möglichen Sicherheitsbedrohungen beitragen. In diesem Thema werden einige dieser Bedrohungen erläutert und Empfehlungen bereitgestellt, wie sich vor diesen Bedrohungen schützen lässt. Es beinhaltet auch Informationen dazu, wie sich Microsoft Office-Sicherheitseinstellungen auf Office-Projektmappen auswirken.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Vertrauenswürdiger Code wird in einem neuen, schädlichen Dokument ausgenutzt werden.
 Ein Angreifer könnte vertrauenswürdigen Code, der für einen bestimmten Zweck vorgesehen ist, etwa Herunterladen persönlicher Daten für eine Bewerbung, übernehmen und in einem anderen Dokument, z. B. einem Arbeitsblatt, erneut verwenden. Der Code weiß nicht, dass nicht das Originaldokument ausgeführt wird, und begünstigt möglicherweise andere Bedrohungen, etwa Offenlegung persönlicher Daten oder Ausführen von Code mit erweiterten Berechtigungen, wenn er von einem anderen Benutzer geöffnet wird. Alternativ kann der Angreifer die Daten im Arbeitsblatt ändern, sodass beim Senden an das Opfer auf unerwartete Weise verhält. Durch Ändern der Werte, Formeln oder Darstellungsmerkmale eines mit Code verknüpften Arbeitsblatts wird es einem böswilligen Benutzer ermöglicht, einen anderen Benutzer durch Senden einer geänderten Datei anzugreifen. Außerdem können Benutzer durch Ändern von Werten auf dem Arbeitsblatt möglicherweise auf Informationen zugreifen, die nicht für sie bestimmt sind.

 Da sowohl der Speicherort der Assembly als auch der des Dokuments über ausreichende Beweise verfügen müssen, damit die Ausführung erfolgt, ist dieser Angriff nicht leicht zu bewerkstelligen. Beispielsweise haben Dokumente in E-Mail-Anhängen oder auf nicht vertrauenswürdigen Intranetservern nicht genügend Berechtigungen, um ausgeführt zu werden.

 Damit dieser Angriff möglich ist, muss der Code selbst so geschrieben sein, dass er Entscheidungen auf der Grundlage potenziell nicht vertrauenswürdiger Daten trifft. Ein Beispiel hierfür ist das Erstellen eines Arbeitsblatts mit einer ausgeblendeten Zelle, die den Namen eines Datenbankservers enthält. Der Benutzer übermittelt das Arbeitsblatt an eine ASPX-Seite, die versucht, mit der SQL-Authentifizierung und einem hardcodierten SA-Kennwort eine Verbindung zu diesem Server aufzubauen. Ein Angreifer könnte den Inhalt der ausgeblendeten Zelle durch einen anderen Computernamen ersetzen und so das SA-Kennwort abrufen. Um dieses Problem zu vermeiden, sollten Sie niemals Kennwörter hartcodieren und stets die Server-IDs vor dem Zugriff auf den Server mit einer internen Liste vertrauenswürdiger Server abgleichen.

### <a name="recommendations"></a>Empfehlungen

- Überprüfen Sie immer Eingaben und Daten, egal, ob sie vom Benutzer, aus dem Dokument, aus einer Datenbank, von einem Webdienst oder aus einer anderen Quelle stammen.

- Achten Sie darauf, dass Sie bestimmte Arten von Funktionen nicht offen zugänglich machen, beispielsweise das Abrufen privilegierter Daten im Namen des Benutzers und Ablegen dieser Daten auf einem ungeschützten Arbeitsblatt.

- Je nach Typ der Anwendung ist es möglicherweise sinnvoll, vor dem Ausführen von irgendwelchem Code zu überprüfen, ob das Originaldokument ausgeführt wird. Vergewissern Sie sich sich beispielsweise, dass der Code aus einem Dokument ausgeführt wird, das in einem bekannten, sicheren Speicherort gespeichert ist.

- Eventuell ist es sinnvoll, beim Öffnen des Dokuments eine Warnung anzuzeigen, wenn Ihre Anwendung privilegierte Aktionen ausführt. Sie können zum Beispiel einen Begrüßungsbildschirm oder ein Startdialogfeld erstellen, in dem mitgeteilt wird, dass die Anwendung auf persönliche Daten zugreift, und dem Benutzer die Entscheidung zum Fortsetzen oder Abbrechen überlassen. Wenn ein Endbenutzer eine solche Warnung aus einem scheinbar unverfänglichen Dokument erhält, kann er die Anwendung beenden, bevor es irgendeine Beeinträchtigung gibt.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Code wird von der Outlook-Objektmodellschutz blockiert.
 In Microsoft Office kann verhindert werden, dass Code bestimmte Eigenschaften, Methoden und Objekte im Objektmodell verwendet. Durch Einschränken des Zugriffs auf diese Objekte, können Outlook, um zu verhindern, dass e-Mail-Würmer und-Viren das Objektmodell für böswillige Zwecke verwenden. Dieses Sicherheitsfeature wird als Outlook-Objektmodellschutz bezeichnet. Wenn ein VSTO-Add-in versucht, eine beschränkte Eigenschaft oder Methode verwenden, während der Objektmodellschutz aktiviert ist, zeigt Outlook eine sicherheitswarnung angezeigt, die mit der Benutzer den Vorgang zu beenden oder ermöglicht es dem Benutzer das Gewähren von Zugriff auf die Eigenschaft oder Methode für einen begrenzten Zeitraum t IME. Wenn der Benutzer den Vorgang beendet, lösen Outlook-VSTO-Add-Ins, die als Office-Projektmappen in Visual Studio erstellt wurden, eine <xref:System.Runtime.InteropServices.COMException>aus.

 Der Objektmodellschutz kann VSTO-Add-Ins auf unterschiedliche Weise beeinflussen, abhängig davon, ob Outlook mit Microsoft Exchange Server verwendet wird:

- Wird Outlook ohne Exchange verwendet, kann ein Administrator den Objektmodellschutz für alle VSTO-Add-Ins auf dem Computer aktivieren bzw. deaktivieren.

- Wenn Outlook mit Exchange verwendet wird, kann ein Administrator den Objektmodellschutz für alle VSTO-Add-Ins auf dem Computer aktivieren bzw. deaktivieren, oder er kann angeben, dass bestimmte VSTO-Add-Ins unabhängig vom Objektmodellschutz ausgeführt werden können. Administratoren können auch das Verhalten des Objektmodellschutzes für bestimmte Bereiche des Objektmodells ändern. Beispielsweise können Administratoren automatisch VSTO-Add-ins zum Senden von e-Mails programmgesteuert erlauben, auch wenn der Objektmodellschutz aktiviert ist.

  Beginnend mit Outlook 2007 wurde das Verhalten des Objektmodellschutzes geändert, um die Entwickler- und Benutzerfreundlichkeit zu verbessern, aber gleichzeitig Outlook zu schützen. Weitere Informationen finden Sie unter [Code Security Changes in Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).

### <a name="minimize-object-model-guard-warnings"></a>Minimieren der Warnungen vom Objektmodellschutz
 Damit Sicherheitswarnungen vermieden werden, wenn Sie beschränkte Eigenschaften und Methoden verwenden, müssen Sie sicherstellen, dass das VSTO-Add-In Outlook-Objekte aus dem `Application` -Feld der `ThisAddIn` -Klasse im Projekt abruft. Weitere Informationen über dieses Feld finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

 Nur Outlook-Objekten, die aus diesem Objekt abgerufen wurden, kann vom Objektmodellschutz vertraut werden. Im Gegensatz dazu sind Objekte, die aus einem neuen `Microsoft.Office.Interop.Outlook.Application`-Objekt abgerufen wurden, nicht vertrauenswürdig, sodass die beschränkten Eigenschaften und Methoden Sicherheitswarnungen auslösen, wenn der Objektmodellschutz aktiviert ist.

 Im folgenden Codebeispiel wird eine Sicherheitswarnung angezeigt, wenn der Objektmodellschutz aktiviert wird. Die `To`-Eigenschaft der `Microsoft.Office.Interop.Outlook.MailItem`-Klasse wird durch den Objektmodellschutz beschränkt. Die `Microsoft.Office.Interop.Outlook.MailItem` Objekt ist nicht vertrauenswürdig, da der Code Ruft ab, aus einer `Microsoft.Office.Interop.Outlook.Application` , erstellt wird, mit der **neue** -Operator, sondern aus der `Application` Feld.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Im folgenden Codebeispiel wird veranschaulicht, wie Sie den eingeschränkten verwenden, um die Eigenschaft eine `Microsoft.Office.Interop.Outlook.MailItem` -Objekt, das den Objektmodellschutz vertrauenswürdig ist. Im Code wird das vertrauenswürdige `Application`-Feld verwendet, um das `Microsoft.Office.Interop.Outlook.MailItem`-Objekt abzurufen.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Wenn Outlook mit Exchange verwendet wird, ist es nicht möglich, durch ein Abrufen aller Outlook-Objekte aus `ThisAddIn.Application` sicherzustellen, dass Ihr VSTO-Add-In auf das gesamte Outlook-Objektmodell zugreifen kann. Z. B. Wenn Exchange-Administrator Outlook legt automatisch auf Verweigern Sie alle Zugriffsversuche auf Adressinformationen über das Outlook-Objektmodell, und klicken Sie dann die Outlook im vorherigen Codebeispiel wird die Eigenschaft für den Zugriff auf nicht zulässig ist, obwohl im Codebeispiel wird verwendet das vertrauenswürdige `ThisAddIn.Application` Feld.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Geben Sie die Add-ins vertraut, wenn Exchange verwendet wird
 Wenn Outlook mit Exchange verwendet wird, können Administratoren angeben, dass bestimmte VSTO-Add-Ins unabhängig vom Objektmodellschutz ausgeführt werden können. Outlook-VSTO-Add-Ins, die als Office-Projektmappen in Visual Studio erstellt wurden, können nicht einzeln als vertrauenswürdig festgelegt werden, sondern nur als Gruppe.

 Outlook vertraut einem VSTO-Add-in anhand eines Hashcodes der Einstiegspunkt-DLL des VSTO-Add-Ins. Alle Outlook-VSTO-Add-ins, die als Ziel der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verwenden dieselbe Einstiegspunkt-DLL (*"VSTOLoader.dll"*). Dies bedeutet, dass ein Administrator alle VSTO-Add-in vertrauenswürdig einstuft, dessen Ziel die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ausgeführt, unabhängig vom Objektmodellschutz, und klicken Sie dann auf allen anderen VSTO-Add-ins, die auf die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sind ebenfalls vertrauenswürdig. Weitere Informationen zu Vertrauensstellungen für spezielle VSTO-Add-Ins, damit diese unabhängig vom Objektmodellschutz ausgeführt werden können, finden Sie unter [Angeben der Methode zur Verwaltung von Virenschutzfeatures in Outlook](http://go.microsoft.com/fwlink/?LinkId=128773).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Berechtigungsänderungen werden nicht sofort wirksam
 Wenn der Administrator Berechtigungen für ein Dokument oder eine Assembly ändert, müssen die Benutzer alle Office-Anwendungen beenden und dann neu starten, damit die Änderungen wirksam werden.

 Andere Anwendungen, die als Host für Microsoft Office-Anwendungen fungieren, können ebenfalls verhindern, dass die neuen Berechtigungen wirksam werden. Benutzer sollten alle Anwendungen beenden, die Office verwenden (gehostete oder eigenständige), wenn die Sicherheitsrichtlinien geändert wurden.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Trust Center-Einstellungen in Microsoft Office System wirken-Add-ins oder Anpassungen auf Dokumentebene sich nicht
 Benutzer können verhindern, dass VSTO-Add-Ins geladen werden, indem sie eine Option im **Trust Center**festlegen. Allerdings wirken sich diese Vertrauenseinstellungen nicht auf VSTO-Add-Ins aus, die als Office-Projektmappen in Visual Studio erstellt wurden.

 Wenn Benutzer das Laden von VSTO-Add-Ins über das **Trust Center**verhindern, werden die folgenden Typen von VSTO-Add-Ins nicht geladen:

- Verwaltete und nicht verwaltete COM-VSTO Add-Ins

- Verwaltete und nicht verwaltete SmartDocuments

- Verwaltete und nicht verwaltete Automatisierungs-VSTO Add-Ins

- Verwaltete und nicht verwaltete Echtzeitdatenkomponenten

  Die folgenden Verfahren beschreiben, wie Benutzer das **Trust Center** verwenden können, um zu verhindern, dass VSTO-Add-Ins in Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Microsoft Office 2010 geladen werden. Diese Verfahren wirken sich nicht auf VSTO-Add-Ins oder Anpassungen aus, die mit den Office-Entwicklungstools in Visual Studio erstellt wurden.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>So deaktivieren Sie VSTO-Add-Ins in Microsoft Office 2010- und Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Anwendungen

1. Wählen Sie die Registerkarte **Datei** aus.

2. Wählen Sie die *ApplicationName* **Optionen** Schaltfläche.

3. Wählen Sie im Kategorienbereich den Eintrag **Trust Center**aus.

4. Wählen Sie im Detailbereich die Option **Einstellungen für das Trust Center**aus.

5. Wählen Sie im Kategorienbereich den Eintrag **Add-Ins**aus.

6. Wählen Sie im Detailbereich die Option **Anwendungs-Add-Ins müssen von einem vertrauenswürdigen Herausgeber signiert sein** oder **Alle Anwendungs-Add-Ins deaktivieren**aus.

## <a name="see-also"></a>Siehe auch
- [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)
