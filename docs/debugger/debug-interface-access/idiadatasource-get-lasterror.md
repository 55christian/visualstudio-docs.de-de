---
title: 'IDiaDataSource:: get_lastError | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744973"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Ruft den Dateinamen für den letzten Ladefehler ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

vorgenommen Gibt eine Zeichenfolge zurück, die den Namen der PDB-Datei enthält, die dem letzten Ladefehler zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Gibt den letzten Fehlercode zurück, der durch einen Ladevorgang verursacht wurde. Gibt `E_INVALIDARG` zurück, wenn der `pRetVal` Parameter `NULL` ist.

## <a name="example"></a>Beispiel

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)