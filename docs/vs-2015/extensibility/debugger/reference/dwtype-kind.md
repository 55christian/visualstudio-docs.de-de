---
title: DwTYPE_KIND | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f37fb773a07291a883f5cb65e4cb4ac840a87a14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198778"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, wie den Typ des interpretieren eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 TYPE_KIND_METADATA  
 Die [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Union interpretiert werden soll, als eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur.  
  
 TYPE_KIND_PDB  
 Die `TYPE_INFO` Union interpretiert werden soll, als eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur.  
  
 TYPE_KIND_BUILT  
 Die `TYPE_INFO` Union interpretiert werden soll, als eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte dieser Enumeration werden in der `dwKind` Feld der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strukturieren und werden verwendet, um zu bestimmen, wie zum Interpretieren der `type` union-Member. Die `TYPE_INFO` Struktur wird zurückgegeben, durch einen Aufruf der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
