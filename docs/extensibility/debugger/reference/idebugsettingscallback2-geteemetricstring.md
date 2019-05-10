---
title: IDebugSettingsCallback2::GetEEMetricString | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58132d73cd532acd0c89ad5258c6ba4a59b905fa
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458620"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Ruft den Wert von einer Expression Evaluator-Metrik anhand des Namens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parameter
 `guidLang`\

 [in] Eindeutiger Bezeichner der Programmiersprache.

 `guidVendor`\

 [in] Eindeutiger Bezeichner des Herstellers.

 `pszMetric`\

 [in] Der Name der Metrik.

 `pbstrValue`\

 [out] Gibt den Metrikwert-Zeichenfolge zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)