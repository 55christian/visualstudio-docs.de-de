---
title: 'Idiasectioncontrib:: Get_code16bit | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4e9c190108cdbf1eb7be2d21927a95fe56fca75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832469"
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
Ruft ein Flag, das angibt, ob der Abschnitt 16-Bit-Code enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_code16bit(
   BOOL *pRetVal
};
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` ist der Code in den Abschnitt, 16-Bit-; andernfalls, gibt `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode gibt nur auf, wenn der Code 16-Bit ist. Wenn der Code keine 16-Bit ist, konnte es nichts anderes, z. B. 32-Bit oder 64-Bit-Code sein.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)