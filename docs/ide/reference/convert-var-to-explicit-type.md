---
title: Refactoring von Code zum Ersetzen von var durch einen expliziten Typ
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2708bca578b613fac77e9b8ce77b1b2aff8f0945
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968150"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactoring zum Ersetzen von var durch einen expliziten Typ

Mithilfe dieses Refactorings können Sie [var](/dotnet/csharp/language-reference/keywords/var) in einer lokalen Variablendeklaration mit einem expliziten Typ ersetzen.

Dieses Refactoring gilt für:

- C#

## <a name="why-to-use-an-explicit-type"></a>Gründe für die Verwendung eines expliziten Typs

Hier finden Sie einige Gründe für das Deklarieren einer Variable mit einem expliziten Typ:

- Bessere Lesbarkeit des Codes

- Wenn die Variable nicht in der Deklaration initialisiert werden soll

[var](/dotnet/csharp/language-reference/keywords/var) muss jedoch verwendet werden, wenn eine Variable mit einem anonymen Typ initialisiert wird und wenn Sie zu einem späteren Zeitpunkt auf die Eigenschaften des Objekts zugreifen möchten. Weitere Informationen finden Sie unter [Implizit typisierte lokale Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Verwendungsweise

1. Fügen Sie die Einfügemarke in das `var`-Schlüsselwort ein.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Verwenden des Menüs für schnelle Aktionen für den expliziten Typ](media/use-explicit-type.png)

1. Wählen Sie **Expliziten Typ verwenden** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

## <a name="see-also"></a>Siehe auch

- [Implizit typisierte Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)