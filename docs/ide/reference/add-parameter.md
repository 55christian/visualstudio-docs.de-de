---
title: Hinzufügen eines Parameters zu einer Methode mit einer Schnellaktion
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4dbed81809cb3b69814fbf10dde7129b45396eaa
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000195"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hinzufügen eines Parameters zu einer Methode mit einer Schnellaktion

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung:** Ermöglicht das automatische Hinzufügen eines Parameters zu einer Methode basierend auf der Verwendung.

**Hintergrund:** Sie müssen einer Methode einen Parameter hinzufügen und möchten ihn automatisch richtig deklarieren.

**Vorteile**: Sie können den Parameter der Methodendeklaration vor ihrem Aufruf hinzufügen, aber diese Funktion fügt ihn automatisch basierend auf einem Methodenaufruf hinzu.

## <a name="how-to-use-it"></a>Verwendungsweise

1. Fügen Sie einem Methodenaufruf ein zusätzliches Argument hinzu.

   Eine rote Wellenlinie wird unter dem Namen der Methode angezeigt, wo sie aufgerufen wird.

2. Platzieren Sie den Mauszeiger auf der roten Wellenlinie bis das Menü „Schnellaktionen“ angezeigt wird. Wählen Sie den **Pfeil nach unten** im Menü „Schnellaktionen“ aus, und wählen Sie dann **[Methode] Parameter hinzufügen** aus.

   ![Hinzufügen eines Parameters zu einer Methode mit einer Schnellaktion in Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Sie können auch auf das Menü Schnellaktionen zugreifen, indem Sie den Cursor über der Zeile des Methodenaufrufs positionieren und dann **STRG**+ **.** drücken (Punkt) oder auf das Glühbirnensymbol am Rand der Datei klicken.

   Visual Studio fügt den neuen Parameter zur Methodendeklaration hinzu.

> [!NOTE]
> Wenn Sie andere Aufrufe der Methode verwenden, können diese nach der Verwendung dieser Schnellaktion Fehler verursachen, da sie kein Argument für den neu hinzugefügten Parameter angeben.

## <a name="see-also"></a>Siehe auch

- [Hinzufügen eines Parameters zu einem Konstruktor](generate-constructor.md#addparameter)