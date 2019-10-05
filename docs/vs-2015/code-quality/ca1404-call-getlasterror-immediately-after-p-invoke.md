---
title: 'CA1404: GetLastError unmittelbar nach P / Invoke aufrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e33c724d2cebb9423f2e475d95bf42ac5e2cc966
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200316"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: GetLastError unmittelbar nach P/Invoke aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Wird aufgerufen die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> Methode oder die entsprechenden Win32- `GetLastError` -Funktion und der Aufruf, der unmittelbar zuvor sind nicht auf einer Plattform invoke-Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und ist definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut. In der Regel nach einem Fehler nicht verwaltete Funktionen aufrufen, die Win32 `SetLastError` Funktion einen Fehlercode festgelegt, die mit dem Fehler verknüpft ist. Der Aufrufer der fehlerhaften Funktion und ruft die Win32 `GetLastError` -Funktion zum Abrufen des Fehlercodes und ermitteln Sie die Ursache des Fehlers. Der Fehlercode wird auf einer pro-Thread-Basis verwaltet und wird überschrieben, indem der nächste Aufruf von `SetLastError`. Nach ein Aufruf an eine fehlerhafte Aufrufmethode, kann verwalteter Code durch Aufrufen den Fehlercode Abrufen der <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methode. Da der Fehlercode durch interne Aufrufe von anderen verwalteten Methoden der Klassenbibliotheken, überschrieben werden kann die `GetLastError` oder <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> -Methode unmittelbar nach der Plattformaufruf-Methodenaufruf, aufgerufen werden soll.

 Die Regel ignoriert Aufrufe der folgenden verwalteten Member, wenn sie zwischen dem Aufruf von der Plattform invoke-Methode und der Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ändern Sie diese Elemente nicht den Fehler Code und sind nützlich, für den Erfolg der einige Plattform invoke-Methodenaufrufe.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> invoke-Methode, damit den Aufruf von der Plattform unmittelbar folgt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn der Code zwischen dem Aufruf der-Methode aufrufen und die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methodenaufruf kann nicht explizit oder implizit, dass der Fehlercode ändern.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt und eine Methode, die die Regel erfüllt.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1060: Verschieben von P/Invokes in NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke-Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Verwenden Sie verwaltete Entsprechungen der Win32-API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
