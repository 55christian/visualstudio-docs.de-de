---
title: Eine Zuordnung kann nicht erstellt werden &lt;Zuordnungsname&gt; -Eigenschaft wird doppelt aufgeführt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 257490a91ac21868be276cfc3ae5514222dae86d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703838"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Die Zuordnung &lt;Zuordnungsname&gt; kann nicht erstellt werden – Eigenschaft ist zweimal aufgelistet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zuordnung \<Zuordnungsname> kann nicht erstellt werden. Die folgende Eigenschaft ist mehrmals aufgelistet: \<Eigenschaftenname>.  
  
 Zuordnungen werden im Dialogfeld **Zuordnungs-Editor** von den ausgewählten **Zuordnungseigenschaften** definiert. Eigenschaften können für jede Klasse in der Zuordnung nur einmal aufgelistet werden.  
  
 Die Eigenschaft in der Meldung wird in den **Zuordnungseigenschaften** der über- oder untergeordneten Klasse mehrmals aufgeführt.  
  
### <a name="to-resolve-this-condition"></a>So lösen Sie dieses Problem  
  
- Untersuchen Sie die Meldung, und notieren Sie die in der Meldung angegebene Eigenschaft.  
  
- Klicken Sie auf **OK**, um das Meldungsfeld zu schließen.  
  
- Überprüfen Sie die **Zuordnungseigenschaften**, und entfernen Sie die doppelten Einträge.  
  
- Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
