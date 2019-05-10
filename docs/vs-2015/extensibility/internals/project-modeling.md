---
title: Projekt Modellierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0edca4a45419a4a4c962ebf62b65e99c4732a12
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431373"
---
# <a name="project-modeling"></a>Projektmodellierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der nächste Schritt im Bereitstellen von Automatisierung für Ihr Projekt ist, um die standard-Projekt-Objekte zu implementieren: die <xref:EnvDTE.Projects> und `ProjectItems` Auflistungen; die `Project` und <xref:EnvDTE.ProjectItem> Objekte und die übrigen Objekte, die für Ihre Implementierung eindeutig. Diese standard-Objekte werden in Dteinternal.h-Datei definiert. Eine Implementierung der standardmäßigen Objekte wird im Beispiel BscPrj bereitgestellt. Sie können diese Klassen als Modelle verwenden, um Ihre eigenen Objekte für die standard-Projekt zu erstellen, die Seite-an-Seite zu stehen mit Projektobjekten aus anderen Projekttypen.  
  
 Setzt voraus, dass ein automatisierungsbenutzer aufrufen können <xref:EnvDTE.Solution>("`<UniqueProjName>")` und <xref:EnvDTE.ProjectItems> (`n`), wobei n ist eine Indexnummer für ein bestimmtes Projekt in der Lösung abrufen. Dieses Automation-Aufruf führt dazu, dass die Umgebung Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> auf den entsprechenden Projekthierarchie übergeben VSITEMID_ROOT als Element-ID-Parameter und VSHPROPID_ExtObject: VSHPROPID-Parameter. `IVsHierarchy::GetProperty` Gibt eine `IDispatch` Zeiger auf die Bereitstellung der Hauptfunktionen der Automatisierungsobjekt `Project` -Schnittstelle, die Sie implementiert haben.  
  
 Im folgenden finden Sie die Syntax der `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekte Schachtelung aufzunehmen, und Verwenden von Sammlungen zum Erstellen von Gruppen von Projektelementen. Die Hierarchie sieht wie folgt aus.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Schachteln bedeutet, dass eine <xref:EnvDTE.ProjectItem> Objekt kann es sich <xref:EnvDTE.ProjectItems> Auflistung gleichzeitig da eine `ProjectItems` Sammlung kann die geschachtelten Objekte enthalten. Im Beispiel Basic-Projekts wird diese Schachtelung nicht veranschaulicht. Durch die Implementierung der `Project` -Objekts können Sie teilnehmen, in der Baumstruktur, das den Entwurf des allgemeinen Automatisierungsmodells bestimmt.  
  
 Die Projekt-Automatisierung folgt den Pfad in der folgenden Abbildung.  
  
 ![Visual Studio-Projekt-Objekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Projekt-Automatisierung  
  
 Wenn Sie nicht implementieren eine `Project` Objekt ist, wird die Umgebung weiterhin einen generischen zurück `Project` -Objekt, das nur den Namen des Projekts enthält.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>
