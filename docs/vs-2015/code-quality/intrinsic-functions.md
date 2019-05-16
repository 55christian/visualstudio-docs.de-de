---
title: Systeminterne Funktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e5284ae41f961d8e027590b4296037236e7108f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699438"
---
# <a name="intrinsic-functions"></a>Systeminterne Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Ausdruck in SAL kann ein C-/C++-Ausdruck sein, vorausgesetzt, dass es sich um einen Ausdruck handelt, die keine Nebeneffekte haben, wird – z. B. ++,--, und Funktionsaufrufe, die alle haben Nebenwirkungen in diesem Kontext.  SAL bietet jedoch einige funktionsähnliches-Objekte und einige reservierte Symbole, die in SAL-Ausdrücken verwendet werden können. Diese werden als bezeichnet *systeminterne Funktionen*.  
  
## <a name="general-purpose"></a>Allgemeine Verwendung  
 Die folgenden intrinsische funktionsanmerkungen bieten allgemeine-Hilfsprogramm für SAL.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Curr_`|Ein Synonym für das Objekt, das derzeit mit Anmerkungen versehen wird.  Wenn die `_At_` Anmerkung verwendet wird, `_Curr_` ist identisch mit der erste Parameter für `_At_`.  Andernfalls ist er den Parameter oder den gesamten Funktion/Rückgabewert mit dem die Anmerkung lexikalisch zugeordnet ist.|  
|`_Inexpressible_(expr)`|Gibt eine Situation, in dem die Größe eines Puffers zu komplex für den darstellen, indem Sie mithilfe eines Ausdrucks für die Anmerkung ist – z. B. wenn er berechnet wird, durch das Scannen von ein Eingabedataset, und klicken Sie dann zählen Mitglieder ausgewählt.|  
|`_Nullterm_length_(param)`|`param` ist die Anzahl der Elemente im Puffer bis zur, aber nicht einschließlich einen null-Terminator. Sie können auf alle Puffer von nicht-aggregierte, nicht-Void-Typ angewendet werden.|  
|`_Old_(expr)`|Bei der Auswertung in Vorbedingung, `_Old_` gibt den Eingabewert zurück `expr`.  Wenn sie nach der Bedingung ausgewertet wird, wird der Wert `expr` wie es in Vorbedingung ausgewertet worden wären.|  
|`_Param_(n)`|Die `n`-ten Parameter für eine Funktion, die Zählung von 1 bis `n`, und `n` eine literale integrale Konstante ist. Wenn der Parameter benannt ist, ist diese Anmerkung für den Zugriff auf den Parameter anhand des Namens identisch. **Hinweis:** `n` bezieht sich möglicherweise auf die Positionsparameter, die werden durch eine Ellipse definiert, oder können verwendet werden in Funktionsprototypen, in dem Namen nicht verwendet werden.|  
|`return`|Die C/C++-reserviertes Schlüsselwort `return` können in eine SAL-Ausdruck verwendet werden, um den Rückgabewert einer Funktion anzugeben.  Der Wert ist nur verfügbar, im Post-Zustand. Es ist ein Syntaxfehler für die Verwendung in der Pre-Zustand.|  
  
## <a name="string-specific"></a>Spezifisches für Zeichenfolgen  
 Die folgenden Anmerkungen für die systeminterne Funktion aktivieren, Ändern von Zeichenfolgen. Alle vier dieser Funktionen die gleiche Weise unterstützen: die Anzahl der Elemente des Typs zurückgeben, die vor dem ein null-Terminator gefunden wird. Die Unterschiede sind die Arten von Daten in den Elementen, die auf die verwiesen werden. Beachten Sie, die, wenn Sie die Länge der eine Null-terminierte angeben möchten, der als Puffer, nicht Zeichen umfasst, verwenden Sie die `_Nullterm_length_(param)` Anmerkung aus dem vorherigen Abschnitt.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` ist die Anzahl der Elemente in der Zeichenfolge bis zum, aber nicht mit einem null-Terminator. Diese Anmerkung ist für Zeichenfolge-Zeichentypen reserviert.|  
|`strlen(param)`|`param` ist die Anzahl der Elemente in der Zeichenfolge bis zum, aber nicht mit einem null-Terminator. Diese Anmerkung ist reserviert für die Verwendung auf Zeichen arrays und ähnelt der Funktion der C-Laufzeit [strlen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` die Anzahl der Elemente in der Zeichenfolge bis zu (aber nicht einschließlich) ist ein null-Terminator. Diese Anmerkung ist reserviert für die Verwendung in Breitzeichen, arrays und ähnelt der Funktion der C-Laufzeit [wcslen()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen von Kommentaren Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
