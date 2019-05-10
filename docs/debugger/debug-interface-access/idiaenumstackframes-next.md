---
title: 'Idiaenumstackframes:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833303"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Ruft eine angegebene Anzahl von Stack-Frame-Elemente aus der Enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

[in] Die Anzahl der StackFrame-Elemente im Enumerator abgerufen werden sollen.

 rgelt

[out] Ein Array, das mit dem angeforderten gefüllt werden soll, im [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) Objekte.

 pceltFetched

[out] Gibt die Anzahl der Stack-Rahmenelemente enthält in der abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` treten keine weiteren Stapelrahmen. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)