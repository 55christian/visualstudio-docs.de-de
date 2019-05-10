---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df609011250cebc097d3d356242302dbe41f8007
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969084"
---
# <a name="print-command"></a>Befehl „Drucken“

Wertet einen Ausdruck aus oder zeigt angegebenen Text an.

## <a name="syntax"></a>Syntax

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumente

`text`

Erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text

## <a name="remarks"></a>Anmerkungen

Sie können ein Fragezeichen (?) als Alias für diesen Befehl verwenden. Daher wird mit dem Befehl

```cmd
>Debug.Print expA
```

kann beispielsweise auch folgendermaßen geschrieben werden:

```cmd
? expA
```

Beide Versionen dieses Befehls geben den aktuellen Wert des Ausdrucks `expA` zurück.

## <a name="example"></a>Beispiel

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Anweisung auswerten"](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)