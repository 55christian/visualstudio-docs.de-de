---
title: IDiaSymbol::findChildrenExByVA | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6798f3a1dfd8979db926960a6155c5b07e255f21
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149969"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die untergeordneten Elemente des Symbols, die an einer bestimmten virtuellen Adresse gültig sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `symtag`  
 [in] Gibt die symboltags an der untergeordneten Elemente abgerufen werden soll, gemäß der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md). Legen Sie auf `SymTagNull` für alle untergeordneten Elemente abgerufen werden sollen.  
  
 `name`  
 [in] Gibt den Namen der untergeordneten Elemente abgerufen werden sollen. Legen Sie auf `NULL` für alle untergeordneten Elemente abgerufen werden sollen.  
  
 `compareFlags`  
 [in] Gibt die Vergleichsoptionen, die auf Namen angewendet werden. Werte aus der [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) -Enumeration können alleine oder zusammen verwendet werden.  
  
 `address`  
 [in] Gibt die virtuelle Adresse an.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt, das eine Liste der untergeordneten Symbole enthält abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` Wenn mindestens ein untergeordnetes Element des Symbols wurde gefunden, oder gibt zurück, `S_FALSE` , wenn keine untergeordneten Elemente gefunden wurden; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die lokalen Symbole, die zurückgegeben werden enthalten Informationen zum aktiven Bereich.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)
