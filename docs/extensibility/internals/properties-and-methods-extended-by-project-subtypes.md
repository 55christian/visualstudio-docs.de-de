---
title: Eigenschaften und Methoden von Projektuntertypen erweitert | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b944d493e8c7668d331a2db12302cea709df239
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909055"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Eigenschaften und Methoden, die von Projektuntertypen erweitert werden
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einem Projektuntertyp bietet viele Möglichkeiten, um das Verhalten des Projekts zu beeinflussen, da er als Aggregatoren eines Basis-Projekts erstellt wird. In diesem Abschnitt werden einige der Features, die erweitert werden können oder die Projektuntertypen geändert, zusammengefasst.  
  
## <a name="features-gained-by-aggregation"></a>Funktionen, die sich aus der Aggregation ergeben  
 Die folgende Tabelle enthält viele Methoden, die Aggregation erlaubt das Projektuntertypen in Basis-Projekten zu überschreiben.  
  
|Methoden, die durch Aggregation überschreiben|Projektuntertyp|  
|---------------------------------------|---------------------|  
|Von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Ermöglicht einem Projektuntertyp<br /><br /> -Ändern der Beschriftung und das Symbol der Projektknoten.<br />– Überschreiben vollständig Projekt `Browse` Objekt.<br />-Steuern Sie, ob das Projekt umbenannt werden kann.<br />-Control-Sortierreihenfolge.<br />-Control-Benutzerkontext für die dynamische Hilfe.|  
|Von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Ermöglicht einem Projektuntertyp steuern, welche kontextbezogene Dienste für Designer und Editoren bereitgestellt werden.|  
|Von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Ermöglicht einem Projektuntertyp<br /><br /> -Befehlsrouting für Projektbefehle beteiligt.<br />-Hinzufügen, entfernen oder deaktiviert das Ambiente Projektbefehlen und aktive Projektmappen-Explorer-Befehle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Ermöglicht den Projektuntertyp filtern, was in der Benutzer sieht die **neues Element hinzufügen** Dialogfeld.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Ermöglicht einem Projektuntertyp<br /><br /> -Bestimmen Sie den Standardgenerator vorgegebene Dateierweiterung ein.<br />-Ein COM-Objekt einen für Menschen lesbaren generatornamen zuordnen.|  
  
## <a name="properties-used-by-project-subtypes"></a>Eigenschaften, die von Projektuntertypen verwendet werden.  
 Das Projektsystem-Umgebung und Basis mithilfe der Eigenschaften von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> Enumerationen, die in der folgenden Tabelle beschrieben werden, zu einem Projektuntertyp, um verschiedene Funktionen des Projektsystems zu steuern.  
  
|: VSHPROPID-Eigenschaft|Projektuntertyp|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Ermöglicht einem Projektuntertyp steuern den Inhalt der **Element hinzufügen** Dialogfeld. Der Projektuntertyp Geben Sie eine neue Spezifikation der Vorlagenverzeichnisse, neue Arten von Elementen hinzufügen, entfernen Sie vorhandene Elemente und eine Teilmenge der Elemente in des Basisprojekts reorganize kann **Element hinzufügen** Dialogfeld.|  
|`PropertyPagesCLSIDList`|Ermöglicht einem Projektuntertyp hinzufügen oder Entfernen der konfigurationsunabhängigen Eigenschaftenseiten.|  
|`CfgPropertyPagesCLSIDList`|Ermöglicht einem Projektuntertyp hinzufügen oder Entfernen der konfigurationsabhängigen Eigenschaftenseiten.|  
|`ExtObjectCATID`|Ermöglicht einem Projektuntertyp einem Automatisierungsextender für das Projekt oder Objekte bereitstellen, indem die Extender-CATID kennen. Beispielsweise kann einem Projektuntertyp bereitstellen ein benutzerdefinierten `Project.Extender("<subtype>")` Objekt.|  
|`BrowseObjectCATID`|Ermöglicht einem Projektuntertyp zu einem Automatisierungsextender für die `Browse` Objekt, indem Sie kennen die Extender-CATID. Beispielsweise kann einem Projektuntertyp zusätzliche Eigenschaften hinzufügen der <xref:EnvDTE.Project.Properties%2A> Auflistung.|  
|`CfgBrowseObjectCATID`|Ermöglicht einem Projektuntertyp die projektkonfigurationssuchobjekt einem Automatisierungsextender bereit. Beispielsweise kann einem Projektuntertyp zusätzliche Eigenschaften hinzufügen der <xref:EnvDTE.Configuration.Properties%2A> Auflistung.|  
|`CfgExtObjectCATID`|Ermöglicht einem Projektuntertyp das Konfigurationsobjekt ein Automatisierungsextender bereit.|  
|`DefaultPlatformName`|Ermöglicht einem Projektuntertyp, um zu bestimmen, den Namen der Plattform für die Konfigurationsobjekte des Projekts an.|  
  
 Das Basisprojekt stellt eine Standardimplementierung der obigen Eigenschaften bereit. Das Basisprojekt ruft diese durch Aufrufen von `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> auf den äußeren Projektuntertyp, sodass den Projektuntertyp, um die Implementierung der Eigenschaften zu überschreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)
