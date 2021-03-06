---
title: FlowDecision-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b93d88462d5e3984b06c671455439e9bd2b07c5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656689"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision-Aktivitätsdesigner
Der <xref:System.Activities.Statements.FlowDecision>-Knoten ist ein bedingter Knoten, der eine Verzweigung für den Steuerungsverlauf in eine von zwei Alternativen bereitstellt, die auf der Erfüllung einer angegebenen Bedingung basiert. Wenn der Verlauf mehr als zwei Verzweigungen erfordert, verwenden Sie stattdessen <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Der FlowDecision-Knoten
 Verwenden Sie <xref:System.Activities.Statements.FlowDecision>, wenn der Verlauf in zwei Pfade verzweigt werden kann. Ein <xref:System.Activities.Statements.FlowDecision>-Knoten verfügt über ein <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Objekt und ein <xref:System.Activities.Statements.FlowNode>-Objekt, das den beiden möglichen Ergebnissen zugeordnet ist: <xref:System.Activities.Statements.FlowDecision.True%2A> oder <xref:System.Activities.Statements.FlowDecision.False%2A>. Die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Instanz wird ausgewertet, und der Wert dieser Auswertung bestimmt, welcher <xref:System.Activities.Statements.FlowNode>-Knoten als Nächstes innerhalb des <xref:System.Activities.Statements.Flowchart>-Flussdiagramms verarbeitet werden soll.

### <a name="using-the-flowdecision-designer"></a>Verwenden des FlowDecision-Designers
 Der **FlowDecision** -Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die Sie zugreifen können, indem Sie im [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X.)

 Der **FlowDecision** -Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche innerhalb eines **Flowchart** -Aktivitäts Designers abgelegt werden. Dadurch wird eine <xref:System.Activities.Statements.FlowDecision> mit der Bezeichnung " **Decision** " innerhalb der <xref:System.Activities.Statements.Flowchart> Aktivität erstellt. Bewegen Sie den Mauszeiger über den Designer, und die quadratischen Handles **true** und **false** für die beiden Verzweigungen werden angezeigt.

 Nachdem der **FlowDecision** -Designer und andere Designer auf das **Flussdiagramm**gezogen wurden, können die Knoten miteinander verknüpft werden, um die Ausführungsreihenfolge anzugeben. Um einen Link zwischen einem Quellknoten (einschließlich der Verzweigungen **true** und **false** von **FlowDecision**) und einem Zielknoten zu erstellen, bewegen Sie den Mauszeiger über den Designer des Quell Knotens, und auf jeder Seite dieses Knotens werden quadratische Handles angezeigt. Klicken Sie auf eines der quadratischen Handles, und ziehen Sie es mit gedrückter Maustaste zu einem der Handles, die in ähnlicher Weise um den Zielknoten angezeigt werden, wenn Sie den Mauszeiger darüber halten. Lassen Sie die Maustaste los. Daraufhin wird zwischen beiden Knoten einen Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.

 Der Ausdruck, der angibt, dass die <xref:System.Activities.Statements.FlowDecision.Condition%2A> in das Feld **Bedingung** des Fensters **Eigenschaften** eingegeben werden kann, indem Sie auf die Stelle klicken, an der der Hinweis Text "VB-Ausdruck eingeben" lautet.

### <a name="the-flowdecision-properties"></a>Die FlowDecision-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowDecision>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Die Bedingung, die bestimmt, welchen Pfad die Flusssteuerung einschlägt.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Bedingung erfüllt wird.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Bedingung nicht erfüllt wird.|

## <a name="see-also"></a>Siehe auch
 Fluss [Diagramm Fluss](../workflow-designer/flowchart-activity-designers.md) [Diagramm](../workflow-designer/flowchart-activity-designer.md) [\<T >](../workflow-designer/flowswitch-t-activity-designer.md)