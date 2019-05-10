---
title: 'Idiaaddressmap:: Set_imageheaders | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10835f422f8d2d116234eadd91da0d27c424f314
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554221"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Legt image-Header, um die relative virtuelle adressenübersetzung aktivieren.

## <a name="syntax"></a>Syntax

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parameter
 cbData

[in] Anzahl der Bytes der Daten im Anforderungsheader. Muss `n*sizeof(IMAGE_SECTION_HEADER)` , in denen `n` ist die Anzahl der im Abschnittsheader in der ausführbaren Datei.

 data[]

[in] Ein Array von `IMAGE_SECTION_HEADER` Strukturen als die Image-Header verwendet werden soll.

 originalHeaders

[in] Legen Sie auf `FALSE` Wenn die Image-Header aus dem neuen Abbild, sind `TRUE` , wenn sie das ursprüngliche Bild vor einem Upgrade widerspiegeln. Dies würde in der Regel festgelegt werden, um `TRUE` nur in Kombination mit Aufrufe an die [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die `IMAGE_SECTION_HEADER` Struktur wird in "Winnt.h" deklariert, und das Bildformat für die Header von Abschnitt der ausführbaren Datei darstellt.

 Relative virtuelle Adresse Berechnungen hängen von der `IMAGE_SECTION_HEADER` Werte. In der Regel ruft der DIA diese über die Programmdatenbankdatei (.pdb). Wenn diese Werte fehlen, kann die DIA nicht relative virtuelle Adressen zu berechnen und die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) Methodenrückgabe `FALSE`. Der Client muss dann Aufrufen der [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) Methode, um die relative virtuelle Adresse Berechnungen zu ermöglichen, nach dem fehlenden Header von Images aus dem Image selbst bereitstellen.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)