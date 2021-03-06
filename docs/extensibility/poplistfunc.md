---
title: POPLISTFUNC | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3125c17ad30eec6c374c38df7d4baa9e299314a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336222"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Dieser Rückruf wird bereitgestellt, um die [SccPopulateList](../extensibility/sccpopulatelist-function.md) von der IDE und wird durch das Quellcodeverwaltungs-Plug-in verwendet, um eine Liste der Dateien oder Verzeichnisse zu aktualisieren (ebenfalls angegeben wird, um die `SccPopulateList` Funktion).

 Wenn ein Benutzer wählt die **erhalten** Befehl in der IDE, die IDE zeigt eine Liste aller Dateien, die der Benutzer abrufen können. Leider können weiß die IDE nicht, die genaue Liste aller Dateien, die der Benutzer erhalten kann; nur das plug-in enthält diese Liste. Wenn andere Benutzer das Quellcodeverwaltungsprojekt Dateien hinzugefügt haben, sollten diese Dateien in der Liste angezeigt, aber die IDE nicht, welche sie. Die IDE erstellt eine Liste der Dateien, die er davon ausgeht, dass der Benutzer abrufen kann. Bevor sie diese Liste, die dem Benutzer angezeigt wird, ruft es die [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` bietet das Quellcodeverwaltungs-Plug-in eine Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste.

## <a name="signature"></a>Signatur
 Das Quellcodeverwaltungs-Plug-Ins ändert die Liste durch Aufrufen einer IDE implementierte Funktion mit dem folgenden Prototyp:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parameter
 PvCallerData der `pvCallerData` übergebene Parameter vom Aufrufer (der IDE von) der [SccPopulateList](../extensibility/sccpopulatelist-function.md). Das Quellcodeverwaltungs-Plug-in sollte nichts über den Inhalt dieses Parameters voraussetzen.

 fAddRemove Wenn `TRUE`, `lpFileName` ist eine Datei, die die Liste der Dateien hinzugefügt werden sollen. Wenn `FALSE`, `lpFileName` ist eine Datei, die aus der Dateiliste gelöscht werden soll.

 nStatus Status der `lpFileName` (eine Kombination aus der `SCC_STATUS` Bits, finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md) Einzelheiten).

 LpFileName vollständigen Verzeichnispfad der Datei hinzufügen oder aus der Liste löschen.

## <a name="return-value"></a>Rückgabewert

|Wert|Beschreibung|
|-----------|-----------------|
|`TRUE`|Das plug-in kann weiterhin das Aufrufen dieser Funktion.|
|`FALSE`|Es wurde ein Problem auf der Seite der IDE (z. B. eine Out-of Situation Arbeitsspeicher). Die Plug-in-soll Vorgang beendet werden.|

## <a name="remarks"></a>Hinweise
 Für jede Datei, die das Quellcodeverwaltungs-Plug-In hinzufügen oder aus der Liste löschen möchte, ruft diese Funktion auf, übergibt die `lpFileName`. Die `fAddRemove` Flag gibt an, eine neue Datei hinzugefügt oder eine alte Datei zu löschen. Die `nStatus` Parameter enthält den Status der Datei. Wenn es sich bei SCC-Plug-In hinzufügen und Löschen von Dateien abgeschlossen ist, gibt er aus der [SccPopulateList](../extensibility/sccpopulatelist-function.md) aufrufen.

> [!NOTE]
> Die `SCC_CAP_POPULATELIST` Funktion Bit ist für Visual Studio erforderlich.

## <a name="see-also"></a>Siehe auch
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Datei-Statuscode](../extensibility/file-status-code-enumerator.md)