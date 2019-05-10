---
title: Symbole und Symboltags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6affc24a84ef4d008ece5f95e45a11eb70f33b4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854711"
---
# <a name="symbols-and-symbol-tags"></a>Symbole und Symboltags
Debuginformationen zu kompiliertes Programm wird als Symbole, die mithilfe der Debug Interface Access (DIA)-SDK-APIs zugegriffen werden kann, in die Programmdatenbankdatei (PDB) gespeichert. Alle Symbole haben ein [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) und [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) Eigenschaft. Die `symTag` Eigenschaft gibt die Art des Symbols an, gemäß der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration. Die `symIndexId` -Eigenschaft ist eine `DWORD` -Wert, der den eindeutigen Bezeichner für jede Instanz eines Symbols enthält.

 Symbole verfügen auch über Eigenschaften, die zusätzliche Informationen zu den Symbol sowie Verweise auf andere Symbole, meistens angeben, können eine [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) oder [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Wenn Sie eine Eigenschaft, die einen Verweis enthält Abfragen, wird der Verweis zurückgegeben, als ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt. Diese Eigenschaften werden immer zusammen mit einer anderen Eigenschaft von dem gleichen Namen und dem Suffix mit "Id", z. B. [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) und [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Die Tabellen in [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md), [lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), und [Hierarchie der Symboltypen Klasse](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) beschreiben Sie die Eigenschaften für jede der verschiedenen Arten von Symbole. Diese Eigenschaften möglicherweise die relevanten Informationen oder Verweise auf andere Symbole. Da die `*Id` Eigenschaften sind einfach numerische Ordinalzahl Bezeichner ihrer zugehörigen Eigenschaften, die sie über weitere Diskussionen ausgelassen werden. Sie sind bezeichnet nur, wenn für die Erläuterung der Parameter erforderlich.

 Beim Versuch, die Eigenschaft zuzugreifen, wenn kein Fehler auftritt und die Symbol-Eigenschaft einen Wert zugewiesen wurde, der Eigenschaft "get"-Methode `S_OK`. Der Rückgabewert `S_FALSE` gibt an, dass die Eigenschaft für das aktuelle Symbol ungültig ist.

## <a name="in-this-section"></a>In diesem Abschnitt

[Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)

Beschreibt die verschiedenen Arten von Standorten, die ein Symbol verwenden kann.

[Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Beschreibt die Symboltypen, die lexikalische Hierarchien wie z. B. Dateien, Module und Funktionen bilden.

[Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Beschreibt die Symboltypen, die auf der anderen Sprachelemente entsprechen, z. B. Klassen, Arrays und Funktion Typen zurückgeben.

## <a name="see-also"></a>Siehe auch

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)