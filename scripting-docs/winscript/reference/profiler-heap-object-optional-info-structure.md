---
title: PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c7f28499b5d6e1e01caab1e6fd83fc5ab72ccf6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823865"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur
Stellt optionale Informationen über Heapobjekte dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Member  
  
|Member|Typ|Beschreibung|  
|------------|----------|-----------------|  
|infoType|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE-Enumeration](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Der Typ der optionale Informationen.|  
|Prototyp|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des das heapobjekt Prototype-Objekt.|  
|functionName|LPCWSTR|Das heapobjekt Funktionsname.|  
|elementAttributesSize|UINT|Die Größe des die Attribute des Heapobjekts-Element.|  
|elementTextChildrenSize|UINT|Die Größe der untergeordneten Elemente des Heapobjekts-Text.|  
|scopeList|[PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Das heapobjekt Bereichsliste.|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Das heapobjekt interne Eigenschaften.|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Eigenschaften des Heapobjekts.|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Eigenschaften des Heapobjekts.|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Beziehungen für das heapobjekt.|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Eine Liste der Ereignisse die heapobjekt.|