---
title: 'Idiaenumsegments:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff4c5d26d875dc098775d0d379e7d12b062801cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840017"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer Enumerationsfolge.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 celt

[in] Die Anzahl der Segmente in der Enumerationsfolge übersprungen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` treten keine weiteren Segmente mehr überspringen.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)