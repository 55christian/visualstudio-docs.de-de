---
title: Befehl "Neue Datei"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a71a6d313ce12a40cd5c30470f53b1e2a1b69e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919119"
---
# <a name="new-file-command"></a>Befehl "Neue Datei"
Erstellt eine neue Datei und öffnet sie. Die Datei wird unter „Sonstige Dateien“ (Ordner) angezeigt.

## <a name="syntax"></a>Syntax

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumente
`filename`

Optional. Der Name der Datei. Wenn kein Name angegeben wird, wird ein Standardname bereitgestellt. Wenn kein Vorlagenname aufgeführt ist, wird eine Textdatei erstellt.

## <a name="switches"></a>Schalter
/t:`templatename`\
Optional. Gibt den Typ der zu erstellenden Datei an.

Die Argumentsyntax /t:`templatename` gibt die im Dialogfeld „Neue Datei“ gefundenen Informationen wieder. Geben Sie den Namen der Kategorie gefolgt von einem umgekehrten Schrägstrich (`\`) und den Vorlagennamen ein. Setzen Sie außerdem die komplette Zeichenfolge in Anführungszeichen.

Um z.B. eine neue [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Quelldatei zu erstellen, müssen Sie für das Argument /t:`templatename` Folgendes eingeben:

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Dieses Beispiel zeigt, dass sich die C++-Dateivorlage unter der Kategorie Visual C++ im Dialogfeld **Neue Datei** befindet.

/e:`editorname`\
Optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.

Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld „Öffnen mit“ angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.

Geben Sie zum Öffnen einer Datei im Quellcode-Editor für das Argument /e:`editorname` beispielsweise Folgendes ein:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Beispiel
Durch dieses Beispiel wird eine neue Webseite namens „test1.htm“ erstellt und im Quellcode-Editor geöffnet.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Direktfenster](../../ide/reference/immediate-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)