---
title: DiaAddressMapEntry | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 311762f4eafc8dad63da5854870f2836ee68b3ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554895"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Beschreibt einen Eintrag in einer-Adresszuordnung an.

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elements
`rva` Eine relative virtuelle Adresse (RVA) in Abbildung A.

`rvaTo` Die relative virtuelle Adresse `rva` in Abbildung b zugeordnet ist

## <a name="remarks"></a>Hinweise
Eine Adresszuordnung enthält eine Übersetzung aus einem Image-Layout (A) in einem anderen (B). Ein Array von `DiaAddressMapEntry` Strukturen, sortiert nach `rva` definiert eine Adresszuordnung.

Um eine Adresse zu übersetzen `addrA`, in der Abbildung ein in eine Adresse `addrB`, führen Sie in Abbildung B die folgenden Schritte aus:

1. Suchen Sie die Zuordnung für den Eintrag, `e`, mit dem größten `rva` kleiner als oder gleich `addrA`.

2. Legen Sie `delta = addrA - e.rva` fest.

3. Legen Sie `addrB = e.rvaTo + delta` fest.

    Ein Array von `DiaAddressMapEntry` Strukturen übergeben wird, um die [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: dia2.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
