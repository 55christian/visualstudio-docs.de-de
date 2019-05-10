---
title: 'CA2001: Keine problematischen Methoden aufrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26f50580c8d29e24b25a9dad520a81d22a3dfc0c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958711"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Keine problematischen Methoden aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.

## <a name="rule-description"></a>Regelbeschreibung
 Vermeiden Sie überflüssige und möglicherweise gefährliche Methodenaufrufe.

 Ein Verstoß gegen diese Regel tritt auf, wenn ein Member einer der folgenden Methoden aufruft.

|Methode|Beschreibung|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Aufrufen von GC aus. Erfassen, kann die Anwendungsleistung erheblich beeinträchtigen und ist nur selten notwendig. Weitere Informationen finden Sie unter den [Mariani's Performance Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) Blogeintrag auf MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend und Thread.Resume sind aufgrund ihrer zu unvorhersehbarem Verhalten veraltet.  Verwenden Sie andere Klassen in der <xref:System.Threading> -Namespace, z. B. <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, und <xref:System.Threading.Semaphore> auf Threads zu synchronisieren oder Ressourcen zu schützen.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die Methode DangerousGetHandle stellt ein Sicherheitsrisiko dar, da es ein Handle zurückgeben kann, der ungültig ist. Finden Sie unter den <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> und <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Methoden für die Weitere Informationen dazu, wie Sie die Methode DangerousGetHandle sicher zu verwenden.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können die Assemblys an unerwarteten Speicherorten laden. Siehe beispielsweise Suzanne Cook die Anmerkungen zu dieser Version .NET CLR-Blogbeiträge [LoadFile Visual Studio. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) und [Auswählen einer Bindungskontexts](http://go.microsoft.com/fwlink/?LinkId=164451) auf der MSDN-Website für Informationen zu Methoden, die Assemblys zu laden.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Beim Start der Benutzercode in einem verwalteten Prozess ausführen, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen. Die common Language Runtime (CLR) führt Initialisierungsaktionen aus, die adressiert, der die P/Invoke-Benutzer verhindern können.<br /><br /> Wenn Sie zum Aufrufen von CoSetProxyBlanket für eine verwaltete Anwendung verfügen, empfehlen wir, dass Sie starten Sie den Prozess mit einer nativen Code (C++) ausführbaren, im nativen Code CoSetProxyBlanket, und klicken Sie dann Ihre Anwendung mit verwaltetem Code im Prozess. (Achten Sie darauf eine Versionsnummer der Common Language Runtime an.)|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder Ersetzen Sie den Aufruf der gefährliche oder problematische Methode aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Nur, wenn keine alternativen für die problematische Methode zur Verfügung stehen, sollten Sie Nachrichten von dieser Regel unterdrücken.

## <a name="see-also"></a>Siehe auch
 [Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)
