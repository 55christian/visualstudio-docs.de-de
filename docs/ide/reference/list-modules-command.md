---
title: Befehl "Module auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595500"
---
# <a name="list-modules-command"></a>Befehl "Module auflisten"
Listet die Module für den aktuellen Prozess auf.

## <a name="syntax"></a>Syntax

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parameter
/Address:`yes|no`

Dies ist optional. Gibt an, ob die Speicheradressen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Name:`yes|no`

Dies ist optional. Gibt an, ob die Namen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Order:`yes|no`

Dies ist optional. Gibt an, ob die Reihenfolge der Module angezeigt werden soll. Der Standardwert ist `no`sein.

/Path:`yes|no`

Dies ist optional. Gibt an, ob die Pfade zu den Modulen angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Process:`yes|no`

Dies ist optional. Gibt an, ob die Prozesse der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

/SymbolFile:`yes|no`

Dies ist optional. Gibt an, ob die Symboldateien der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

/SymbolStatus:`yes|no`

Dies ist optional. Gibt an, ob die Symbolstatus der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Timestamp:`yes|no`

Dies ist optional. Gibt an, ob der Zeitstempel der Module angezeigt werden soll. Der Standardwert ist `no`sein.

/Version:`yes|no`

Dies ist optional. Gibt an, ob die Versionen der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

## <a name="example"></a>Beispiel
In diesem Beispiel werden die Modulnamen, -adressen und -zeitstempel für den aktuellen Prozess aufgeführt.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Vorgehensweise: Verwenden des Modulfensters](../../debugger/how-to-use-the-modules-window.md)
