---
title: Optionen (Vorgängerversion) wird zum schrittweisen Debuggen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f0761ba750146ce7f8cc52e6992dae689f7779
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976962"
---
# <a name="debug-stepping-options-legacy"></a>Optionen zum schrittweisen Debuggen (Vorgängerversion)
In diesem Thema wird beschrieben, wie [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen gedebuggt werden, die gleichzeitig ausgeführte Aktivitäten in der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] aufweisen. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.  
  
 Beim Debuggen von legacyaktivitäten, die gleichzeitig ausgeführt werden, z. B. auf **ParallelActivity** oder **ConditionedActivityGroup**, können Sie eine der beiden folgenden Optionen den Code schrittweise .  
  
- **Einzelschrittausführung des branchens.** In diesem Modus können Sie schrittweise durchlaufen und Debuggen eine bestimmte Verzweigung einer zusammengesetzten Aktivität, z. B. die **ParallelActivity** oder **ConditionalActivityGroup** Aktivität. Wenn Sie diese Option zum Debuggen verwenden, bemerken Sie nicht, dass sich das Steuerungsverhalten ändert, weil andere Aktivitäten im Workflow gleichzeitig ausgeführt werden. Der Debugger durchläuft nur die Aktivitäten in de momentan ausgewähltem Branch schrittweise, während gleichzeitig ggf. andere Aktivitäten des Workflows ausgeführt werden. Beispielsweise wird standardmäßig der Verzweigung ganz links in eine **ParallelActivity** Aktivität und die erste untergeordnete Aktivität eine **ConditionedActivityGroup** Aktivität für die schrittweise Ausführung verwendet werden. Wenn der Benutzer eine andere Verzweigung oder untergeordnete Aktivität debuggen möchte, muss er in der jeweiligen Verzweigung bzw. untergeordneten Aktivität einen expliziten Haltepunkt einfügen. Der Branch wird weiter schrittweise durchlaufen, wenn der Haltepunkt ausgelöst wird.  
  
- **Instanzen Sie Schrittweises Ausführen von.** In diesem Modus können Sie gleichzeitig ausgeführte Aktivitäten des Workflows schrittweise durchlaufen und debuggen. Bei dieser Option ändert sich das Steuerungsverhalten, wenn im Workflow gleichzeitig ausgeführte Aktivitäten aktiv sind.  
  
  Die Option zur schrittweisen Ausführung von Branches ist standardmäßig ausgewählt, und Benutzer können beim Debuggen eines Workflows der Vorgängerversion zwischen den beiden Optionen wechseln.  
  
  Wählen Sie zum Debuggen von Zustandsautomatworkflows der Vorgängerversion die Option zum schrittweisen Ausführen von Instanzen aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen (Vorgängerversion)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)