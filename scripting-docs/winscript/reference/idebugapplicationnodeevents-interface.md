---
title: Idebugapplicationnodeevents-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574718"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents-Schnittstelle
Stellt die Ereignisschnittstelle für die `IDebugApplicationNode`-Schnittstelle bereit.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IDebugApplicationNodeEvents`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Behandelt das-Ereignis, wenn einem Debug-Anwendungs Knoten Objekt ein untergeordneter Knoten hinzugefügt wird.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Behandelt das-Ereignis, wenn ein untergeordneter Knoten aus einem Debug-Anwendungs Knoten Objekt entfernt wird.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Behandelt ein Ereignis, das das Debuggen von Anwendungs Knoten Objekten von einem übergeordneten Knoten bezeichnet.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Behandelt ein Ereignis, das signalisiert, dass das debuganwendungsobjekt an einen übergeordneten Knoten angefügt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)