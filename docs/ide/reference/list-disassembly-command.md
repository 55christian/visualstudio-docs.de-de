---
title: Befehl "Disassemblierung auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747924"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Schalter
Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

/count: `number` [oder] /c: `number` [oder] /length: `number` [oder] /l: `number`

Optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.

/endaddress: `expression` [oder] /e: `expression`

Optional. Adresse, an der die Disassemblierung beendet wird.

/codebytes:`yes`|`no` [oder] /bytes:`yes`|`no` [oder] /b:`yes`|`no`

Optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert ist `no`sein.

/source:`yes`|`no` [oder] /s:`yes`|`no`

Optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert ist `no`sein.

/symbolnames:`yes`|`no` [oder] /names:`yes`|`no` [oder] /n:`yes`|`no`

Optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert ist `yes`sein.

 [/linenumbers:`yes`|`no`]

Optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.

## <a name="example"></a>Beispiel

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)