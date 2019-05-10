---
title: 'Idiastackwalkhelper:: Imageforva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56f71364f28bec56c058a52f5a9e79c6bba298b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837952"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Gibt den Anfang einer ausführbaren Datei des Image im Arbeitsspeicher eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parameter
 `vaContext`

[in] Die virtuelle Adresse, die sich an einer beliebigen Stelle in der ausführbaren Datei Leerzeichen.

 `pvaImageStart`

[out] Gibt zurück, die virtuelle Startadresse des Images von der ausführbaren Datei.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)