---
title: SccCheckout-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5160a2600a8eb3250702dd0836d812b668a3d1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333876"
---
# <a name="scccheckout-function"></a>SccCheckout-Funktion
Wenn eine Liste der vollqualifizierten Dateinamen, checkt diese Funktion sie auf dem lokalen Laufwerk. Der Kommentar gilt für alle Dateien, die ausgecheckt werden. Das kommentarargument möglich einen `null` Zeichenfolge.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 nFiles

[in] Anzahl der Dateien, die ausgecheckt werden sollen.

 lpFileNames

[in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien, die ausgecheckt werden.

 lpComment

[in] Der Kommentar, der auf die einzelnen ausgewählten Dateien ausgecheckt wird, angewendet werden.

 Bestanden

[in] Befehl Flags (finden Sie unter [von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[in] Quellcodeverwaltungs-plug-in spezifischen Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Sehen Sie sich war erfolgreich.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung befindet.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler. Die Datei wurde nicht ausgecheckt.|
|SCC_E_ALREADYCHECKEDOUT|Der Benutzer hat bereits die Datei ausgecheckt haben.|
|SCC_E_FILEISLOCKED|Die Datei ist gesperrt, verbietet die Erstellung neuer Versionen.|
|SCC_E_FILEOUTEXCLUSIVE|Einem anderen Benutzer hat exklusiv ausgecheckt für diese Datei ausgeführt werden.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)