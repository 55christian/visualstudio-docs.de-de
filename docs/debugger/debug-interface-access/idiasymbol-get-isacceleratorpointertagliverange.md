---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8bf20f43fcc8da48a6e1ec1dfd0f65b14f8ad86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62836901"
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Ruft ein Flag, das angibt, ob das Symbol entspricht der *Definition Bereich Symbol* für die Komponente "Tag" einer Zeigervariablen im Code für eine C++-AMP-Beschleuniger kompiliert. Die Definition Bereich Symbol handelt es sich um den Speicherort der eine Variable für eine Spanne von Adressen.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Ein Zeiger auf eine `BOOL` , der angibt, ob das Symbol zum Symbol Bereich Definition entspricht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)