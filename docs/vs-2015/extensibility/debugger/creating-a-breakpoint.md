---
title: Erstellen eines Haltepunkts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cde6d660506e05195ef9f5c0825845cee10ae5c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383477"
---
# <a name="creating-a-breakpoint"></a>Erstellen eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird beschrieben, den Prozess zum Erstellen eines Haltepunkts.  
  
## <a name="methods-in-breakpoint-creation"></a>Methoden in Haltepunkt erstellen  
 Wenn das Modul, das erforderlich ist, um einen Haltepunkt zu binden geladen wird, ruft die Sitzungs-Debug-Manager (SDM) die folgenden Methoden:  
  
1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    > **CanBind** wird nur aufgerufen, wenn ein Benutzer einen Haltepunkt aus dem Fenster "Breakpoints" hergestellt.  
  
4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
