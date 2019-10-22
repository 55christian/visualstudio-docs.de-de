---
title: TEXT_DOCUMENT_ARRAY-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b52b382aa1e91e509672728a3c8f931bfeae27a9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572969"
---
# <a name="text_document_array-structure"></a>TEXT_DOCUMENT_ARRAY-Struktur
Ein Array von [idebugdocumenttext-Schnittstellen](../../winscript/reference/idebugdocumenttext-interface.md) Objekten. Elemente werden mit "cotaskmemzuzuordc" zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Member  
 `dwCount`  
 Die Anzahl der Dokumente.  
  
 `Members`  
 Der Satz von Dokumenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)