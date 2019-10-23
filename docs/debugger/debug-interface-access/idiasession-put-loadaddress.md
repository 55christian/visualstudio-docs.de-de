---
title: IDiaSession::p ut_loadaddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741891"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Legt die Lade Adresse für die ausführbare Datei fest, die den Symbolen in diesem Symbol Speicher entspricht.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parameter
 `NewVal`

in Lade Adresse für die ausführbare Datei.

## <a name="remarks"></a>Hinweise
 Die Eigenschaften der Symbol-virtuellen Adresse (VA) werden mit dem Wert dieser Methode berechnet. Virtuelle Adressen werden nur berechnet, wenn diese Eigenschaft auf einen Wert ungleich 0 (null) festgelegt ist.

> [!NOTE]
> Diese Methode muss aufgerufen werden, wenn Sie das [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt abrufen und bevor Sie mit der Verwendung des-Objekts beginnen, wenn Sie virtuelle Eigenschaften für Symbole verwenden müssen.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)