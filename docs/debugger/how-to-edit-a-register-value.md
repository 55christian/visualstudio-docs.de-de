---
title: 'Vorgehensweise: Bearbeiten eines Register Werts | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ccaa124b64ad462f633e760695f931afaae531
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733420"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Vorgehensweise: Bearbeiten eines Register Werts (C#, C++, Visual Basic, F#)

Das Fenster „Register“ ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.

### <a name="to-change-the-value-of-a-register"></a>So ändern Sie den Wert eines Registers

1. Verschieben Sie die Einfügemarke im Fenster **Register** mithilfe der TAB-TASTE oder der Maus auf den zu ändernden Wert. Wenn Sie mit der Eingabe beginnen, muss sich der Cursor vor dem Wert befinden, der überschrieben werden soll.

2. Geben Sie den neuen Wert ein.

    > [!CAUTION]
    > Das Ändern von Registerwerten (insbesondere im EIP-Register und im EBP-Register) kann sich auf die Ausführung des Programms auswirken.

    > [!CAUTION]
    > Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar unwesentliche Bearbeitung kann Änderungen in einigen Bits mit dem niedrigsten Wert in einem Gleitkommaregister bewirken.

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Verwenden des Fensters "Register"](../debugger/how-to-use-the-registers-window.md)