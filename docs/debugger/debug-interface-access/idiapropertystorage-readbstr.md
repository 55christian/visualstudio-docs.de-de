---
title: IDiaPropertyStorage::ReadBSTR | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0bff81499fe8ea66ce5d4f50616adfec44d3002
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839627"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Liest `BSTR` Werte in einem Eigenschaftensatz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

[in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).

 `pValue`

[out] Gibt den Wert der Eigenschaft zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Gibt `E_INVALIDARG` ist die Eigenschaft nicht vom Typ `BSTR`.

## <a name="remarks"></a>Hinweise
 Ein `BSTR` wird von Windows als 0 (null) endende Breite Zeichenfolge definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)