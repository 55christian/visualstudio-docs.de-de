---
title: 'CA1414: Markieren von booleschen P-Aufrufen von Argumenten mit MarshalAs | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652691"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Platt Form Aufruf Methoden Deklaration enthält einen <xref:System.Boolean?displayProperty=fullName> Parameter oder einen Rückgabewert, aber das <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>-Attribut wird nicht auf den Parameter oder den Rückgabewert angewendet.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mit dem `Declare`-Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> definiert. <xref:System.Runtime.InteropServices.MarshalAsAttribute> gibt das Marshallingverhalten an, das zum Konvertieren von Datentypen zwischen verwaltetem und nicht verwaltetem Code verwendet wird. Viele einfache Datentypen, z. b. <xref:System.Byte?displayProperty=fullName> und <xref:System.Int32?displayProperty=fullName>, haben eine einzelne Darstellung in nicht verwaltetem Code und erfordern keine Angabe des marshallingverhaltens. der Common Language Runtime stellt automatisch das richtige Verhalten bereit.

 Der <xref:System.Boolean>-Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. Wenn die <xref:System.Runtime.InteropServices.MarshalAsAttribute> nicht angegeben ist, wird das standardmäßige Marshallingverhalten für den <xref:System.Boolean> Datentyp <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Dies ist eine 32-Bit-Ganzzahl, die in allen Fällen nicht geeignet ist. Die boolesche Darstellung, die von der nicht verwalteten Methode benötigt wird, sollte bestimmt und mit der entsprechenden <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> abgeglichen werden. UnmanagedType. bool ist der Win32-boolesche Typ, bei dem es sich immer um 4 Bytes handelt. UnmanagedType. U1 sollte für C++ `bool` oder andere 1-Byte-Typen verwendet werden. Weitere Informationen finden Sie unter Standardmäßiges Marshalling [für boolesche Typen](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie <xref:System.Runtime.InteropServices.MarshalAsAttribute> auf den <xref:System.Boolean> Parameter oder den Rückgabewert an. Legen Sie den Wert des-Attributs auf den entsprechenden <xref:System.Runtime.InteropServices.UnmanagedType> fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn das standardmäßige Marshalling-Verhalten angemessen ist, kann der Code leichter verwaltet werden, wenn das Verhalten explizit angegeben wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Platt Form Aufruf Methoden, die mit den entsprechenden <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attributen gekennzeichnet sind.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1901: Deklarationen von P-Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Standardmarshalling für boolesche Typen](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
