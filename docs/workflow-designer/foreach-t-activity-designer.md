---
title: Workflow-Designer - ForEach&lt;T&gt; Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e441898973614b6e3e33fc91d5d9688b51aab7fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949616"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Aktivitäts-Designer

Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert lautet ForEach < Int32\>. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Festlegen der <xref:System.Activities.Statements.ForEach%601.Values%2A>, geben Sie einen Visual Basic-Ausdruck in der **Werte** Feld der **ForEach < T\>**  -Aktivitätsdesigner oder im Eigenschaftenraster.|
|*TypeArgument*|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ForEach%601.Values%2A> durch den generischen Parameter angegebene Sammlung *T*. In der Standardeinstellung *TypeArgument* nastaven NA hodnotu **Int32**. Um den Typ zu ändern, ändern Sie den Wert des der *TypeArgument* Kombinationsfeld im Eigenschaftenraster.|

In der Standardeinstellung der schleifeniterator die Bezeichnung **Element**. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)