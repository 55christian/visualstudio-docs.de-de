---
title: IDiaSymbol::get_frontEndMinor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a23d3aeade62865f768f54eb8face462affee8
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64832765"
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Ruft die Nebenversionsnummer der Front-End ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Nummer der Nebenversion front.end zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Hinweise
 Ein Compiler besteht in der Regel zwei Hauptelemente: die Front-End (den Parser), der verarbeitet, analysiert den Quellcode in ein vorläufiges Formular, und ein Back-End (Codegenerator), konvertiert die vorläufiges Formular in der Assembly. Es ist nicht ungewöhnlich, dass das Front-End, um eine andere Version als das Back-End zu erhalten.

 Ein Front-End oder Back-End-Versionsnummer besteht aus drei Teilen: \<wichtigen >.\< kleinere >. \<erstellen >, wobei \<wichtige > ist die Hauptversionsnummer \<Nebenversion > ist die Nummer der Nebenversion und \<erstellen > ist die Nummer des Builds. Beispiel: 13.10.3077.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)