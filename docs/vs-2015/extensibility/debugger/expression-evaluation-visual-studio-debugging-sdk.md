---
title: Ausdrucksauswertung (Visual Studio Debugging SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562158"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ausdrucksauswertung (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Während des Unterbrechungsmodus muss die IDE um einfache Ausdrücke mit mehreren Variablen des Programms evaluieren können. Um dies zu erreichen, muss die Debug-Engine (DE) analysieren und Auswerten eines Ausdrucks, das in eines der Fenster der IDE eingegeben wird.  
  
 Ausdrücke werden erstellt, mit der [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und sind durch das resultierende dargestellt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.  
  
 Die **IDebugExpression2** Schnittstelle wird implementiert, die DE und ruft seine **EvalAsync** -Methode zur Rückgabe einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, um die IDE, um anzuzeigen die Ergebnisse der Auswertung von Ausdrücken in der IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) gibt eine Struktur, die verwendet werden kann, können Sie den Wert eines Ausdrucks in einem Überwachungsfenster oder das Fenster "lokal" zurück.  
  
 Ruft die Debug-Pakets oder einer Sitzung Debug-Manager (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) oder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die darstellt Das Ergebnis der Auswertung. `IDebugProperty2` verfügt über Methoden, die den Namen, Typ und Wert des Ausdrucks zurückgeben. Diese Informationen werden in den verschiedenen Debuggerfenstern angezeigt.  
  
## <a name="using-expression-evaluation"></a>Verwenden die Auswertung von Ausdrücken  
 Um die Auswertung des Ausdrucks verwenden zu können, müssen Sie implementieren die [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) -Methode und alle Methoden von der [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, wie in der folgenden Tabelle gezeigt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet einen Ausdruck asynchron an.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone ausdrucksauswertung.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet einen Ausdruck synchron an.|  
  
 Synchrone und asynchrone Auswertung erfordern die Implementierung der [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Asynchrone ausdrucksauswertung erfordert die Implementierung von [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
