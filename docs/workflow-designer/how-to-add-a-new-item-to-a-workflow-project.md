---
title: 'Workflow-Designer: Hinzufügen eines neuen Elements zum Projekt des Workflows'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29e4c03eef2a276995890bbd6b723fa457aefde2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432036"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt

Nachdem Sie ein Workflowprojekt erstellt haben, können Sie die Workflowaktivitäten, Designer und andere bekannte Visual Studio-Elemente zu Ihrem Projekt hinzufügen.

Die folgende Tabelle enthält die Windows Workflow Foundation (WF)-Elemente, die Sie zu einem Workflowprojekt hinzufügen können:

| Name | Beschreibung |
|-| - |
| Aktivität | Eine Aktivität, die aus anderen Aktivitäten besteht. Durch die Auswahl dieses Elements die gleiche XAML-Datei dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsbibliothek** Vorlage für ein neues Projekt. Weitere Informationen zu dieser Vorgehensweise finden Sie unter [erstellen ein Workflowprojekts](creating-a-workflow-project.md). |
| Aktivitätsdesigner | Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements die gleichen Dateien dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitäts-Designerbibliothek** Vorlage für ein neues Projekt. |
| Codeaktivität | Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert. |
| WCF-Workflowdienst | Ein [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements die gleichen Dateien dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **WCF-Workflowdienstanwendung** Vorlage für ein neues Projekt. Weitere Informationen über diese Prozedur finden Sie unter [Vorgehensweise: Erstellen eine Dienstanwendung für WCF-Workflows](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Wählen Sie im linken Bereich die **Workflow** Kategorie, und wählen Sie dann eine Elementvorlage für den Workflow.

   > [!NOTE]
   > Wenn Sie nicht sehen die **Workflow** Kategorie, der ersten Installation der **Windows Workflow Foundation** Komponente von Visual Studio. Ausführliche Anweisungen finden Sie unter [Installieren von Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Geben Sie einen Namen für das Element in der **Namen** Feld am unteren Rand des Dialogfelds.

1. Wählen Sie **hinzufügen** das Element dem Projekt hinzugefügt.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)