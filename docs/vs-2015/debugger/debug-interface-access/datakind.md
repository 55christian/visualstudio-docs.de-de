---
title: DataKind | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197632"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, die bestimmten Bereich eines Datenwerts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elements  
 DataIsUnknown  
 Symbol "Daten" kann nicht bestimmt werden.  
  
 DataIsLocal  
 Datenelement ist eine lokale Variable.  
  
 DataIsStaticLocal  
 Datenelement ist eine statische lokale Variable.  
  
 DataIsParam  
 Datenelement ist ein formaler Parameter.  
  
 DataIsObjectPtr  
 Datenelement ist einem Zeiger (`this`).  
  
 DataIsFileStatic  
 Datenelement ist eine Variable im Bereich einer Datei.  
  
 DataIsGlobal  
 Datenelement ist eine globale Variable.  
  
 DataIsMember  
 Datenelement ist eine Objektvariable des Elements.  
  
 DataIsStaticMember  
 Datenelement ist eine statische Klasse-Variable.  
  
 DataIsConstant  
 Datenelement ist ein konstanter Wert.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch die [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
