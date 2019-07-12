---
title: 'Idiasymbol:: Get_typeids | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7b32ab5b1965ea7a641cfac470addd2aae0ede0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64791766"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Ruft ein Array von Compiler-spezifischer Typ-ID-Werten für dieses Symbol ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parameter
 `cTypeIds`

[in] Die Größe des Puffers zum Speichern der Daten.

 `pcTypeIds`

[out] Gibt die Anzahl der `typeIds` geschrieben, oder wenn `typeIds` ist `NULL`, klicken Sie dann die Gesamtzahl der Typ-IDs zur Verfügung.

 `typeIds[]`

[out] Ein Array, das sich mit dem Typ-IDs gefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)