---
title: IDiaStackWalkFrame::readMemory | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82ef0d25e796f9e04ecdcfd0c54a7312b9c9edad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837913"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Liest Arbeitsspeicher aus Image an.

## <a name="syntax"></a>Syntax

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parameter
 `type`

[in] Eines der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumerationswerte, der angibt, die Art des Arbeitsspeichers auf.

 `va`

[in] Speicherort der virtuellen Adresse in Abbildung gelesen werden soll.

 `cbData`

[in] Größe des Datenpuffers in Byte.

 `pcbData`

[out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes der Daten zur Verfügung.

 `data`

[out] Ein Puffer, der mit Daten aus der angegebenen Position gefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)