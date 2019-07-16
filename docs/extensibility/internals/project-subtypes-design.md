---
title: Projekt Untertypen Entwurf | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dee113f16e43be95e456f1f6189b4922b2d3e926
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328246"
---
# <a name="project-subtypes-design"></a>Entwurf von Projektuntertypen

Projektuntertypen können VSPackages, Projekte, die basierend auf der Microsoft Build Engine (MSBuild) zu erweitern. Die Verwendung der Aggregation ermöglicht Ihnen die Wiederverwendung der größte Teil das verwaltete Core-Projektsystem implementiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] noch immer noch das Verhalten für ein bestimmtes Szenario anpassen.

 In den folgenden Themen beschreiben den grundlegenden Aufbau und die Implementierung von Projektuntertypen:

- Untertyp Projektentwurf.

- Die Aggregation mit mehreren Ebenen.

- Unterstützende Schnittstellen.

## <a name="project-subtype-design"></a>Untertyp Projektentwurf

Die Initialisierung von einem Projektuntertyp erfolgt durch das Zusammenfassen der Hauptseite <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Objekte. Diese Aggregation ermöglicht einem Projektuntertyp zu überschreiben, oder erhöhen die meisten Funktionen des Basisprojekts. Projektuntertypen Abrufen der ersten Gelegenheit verlassen, Eigenschaften, die mit behandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, Befehle mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>, und Verwenden von Project Item Management <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Projektuntertypen können erweitern:

- Projekt-Konfigurationsobjekte.

- Konfigurationsabhängig-Objekte.

- Durchsuchen der konfigurationsunabhängigen-Objekte.

- Projekt-Automation-Objekte.

- Teamprojektsammlungen Sie Automation-Eigenschaft.

Weitere Informationen zur Erweiterbarkeit von Projektuntertypen finden Sie unter [Eigenschaften und Methoden von Projektuntertypen erweitert](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Richtliniendateien

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung bietet ein Beispiel für das Basisprojektsystem mit einem Projektuntertyp in seiner Implementierung von Richtliniendateien zu erweitern. Eine Richtliniendatei ermöglicht das Strukturieren der der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung durch die Verwaltung von Features, die im Projektmappen-Explorer enthalten **Projekt hinzufügen** im Dialogfeld **neues Element hinzufügen** Dialogfeld und der  **Eigenschaften** Dialogfeld. Der Untertyp der Richtlinie überschrieben und erweitert diese Funktionen auch über <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Implementierungen.

### <a name="aggregation-mechanism"></a>Aggregation-Mechanismus

Der Umgebung Projekt Untertyp Aggregation Mechanismus unterstützt mehrere Ebenen von Aggregation, sodass eine erweiterte Untertyp für die Implementierung weiterer flavoring ein Projekt. Darüber hinaus die unterstützende Objekte eines Projekts Untertyp, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, ermöglichen es mehrere Ebenen von Schichten. In Übereinstimmung mit den Einschränkungen des COM- und COM müssen Aggregationsregeln, Projektuntertypen und des Basisprojekts kooperativ programmiert werden, um den inneren Untertyp oder dem Basisprojekt ordnungsgemäß beim Delegieren der Methodenaufrufe, und Verwalten von Verweiszähler teilnehmen kann . Zur Unterstützung der Aggregation programmiert werden, also muss das Projekt zu aggregiert werden.

Die folgende Abbildung zeigt eine schematische Darstellung einer mehrstufigen Projekt Untertyp Aggregation.

![Grafik zu Visual Studio-Mehrebenen-Projekttyp](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Eine auf mehreren Ebenen Projekt Untertyp Aggregation besteht aus drei Ebenen enthält, ein Basis-Projekt, das von einem Projektuntertyp aggregiert, wird durch eine erweiterte Projektuntertyp weiter aggregiert. In der Abbildung konzentriert sich auf einige unterstützenden Schnittstellen, die im Rahmen der bereitgestellt werden die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Untertyp Projektarchitektur.

### <a name="deployment-mechanisms"></a>Mechanismen zur Bereitstellung

Zu viele das Basisprojektsystem gehören Funktionen, die von einem Projektuntertyp erweiterte Mechanismen zur Bereitstellung von. Einem Projektuntertyp wirkt sich auf Mechanismen zur Bereitstellung von Konfigurationsschnittstellen implementieren (z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), werden abgerufen, indem Sie QueryInterface für Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. In einem Szenario, in dem sowohl für den Projektuntertyp als auch für den erweiterten Projektuntertyp andere Konfiguration-Implementierungen hinzufügen, ruft das Basisprojekt `QueryInterface` auf des erweiterten projektuntertyps `IUnknown`. Wenn der inneren Projektuntertyp die Implementierung für die Konfiguration, der das Basisprojekt angefordert wird enthält, der erweiterte Projektuntertyp, die an die Implementierung von der inneren Projektuntertyp delegiert werden. Implementieren Sie als Mechanismus zum Status von Aggregationsebene ein in eine andere beibehalten, alle Ebenen von Projektuntertypen <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> beziehen Sie XML-Daten in den Projektdateien, nicht mit dem Build beibehalten werden. Weitere Informationen finden Sie unter [beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> wird als Mechanismus zum Abrufen von Automatisierungsextendern aus der Projektuntertypen implementiert.

Die folgende Abbildung konzentriert sich auf die Automation-Extender-Implementierung, die projektkonfigurationssuchobjekt vor allem von Projektuntertypen verwendet werden, um das Basisprojektsystem zu erweitern.

![Grafik zu VS-Projekttyp Automatisierungsextender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Projektuntertypen können das Basisprojektsystem durch Erweitern des Automatisierungsmodells für das Objekt weiter erweitern. Diese werden als Teil des DTE-Automatisierungsobjekt definiert und dienen zum Erweitern der Project-Objekt, das `ProjectItem` Objekt und die `Configuration` Objekt. Weitere Informationen finden Sie unter [Erweitern des Objektmodells des Projekts Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Mit mehreren Ebenen Aggregation

Eine Implementierung der Projekt-Untertyp, die eine niedrigere Ebene Projektuntertyp umschließt muss kooperativ programmiert werden, um die ordnungsgemäße Funktion den inneren Projektuntertyp zulassen. Eine Liste der Aufgaben Programmieren enthält:

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung des projektuntertyps, die den inneren Untertyp umschlossen wird, muss zum Delegieren der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> der inneren Projektuntertyp-Implementierung für beide <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> Methoden.

- Die <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des projektuntertyps Wrapper muss an, die von der inneren Projektuntertyp delegieren. Insbesondere für die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> muss die Zeichenfolge mit den Namen der von der inneren Projektuntertyp und verkettet Sie dann die Zeichenfolgen, die als Extender hinzufügen möchte.

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> -Implementierung von einem Projektuntertyp Wrapper instanziieren muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> Objekt der inneren Projektuntertyp und halten Sie ihn als einen privaten Delegaten, da nur das Basisprojekt projektkonfigurationsobjekt direkt weiß, dass der Wrapper Projektuntertyp-Konfigurationsobjekt vorhanden ist. Äußeren Projektuntertyp kann anfänglich Konfigurationsschnittstellen direkt behandeln möchte, und Delegieren dann den Rest der inneren Projektuntertyp-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.

## <a name="supporting-interfaces"></a>Unterstützende Schnittstellen

Das Basisprojekt delegiert Aufrufe zu unterstützenden Schnittstellen hinzugefügt, die von einem Projektuntertyp, um verschiedene Aspekte der Implementierung zu erweitern. Dies schließt die Projekt-Konfigurationsobjekte und den verschiedenen Eigenschaft Objektkatalog: Objekte erweitern. Diese Schnittstellen werden abgerufen, durch den Aufruf `QueryInterface` auf `punkOuter` (ein Zeiger auf die `IUnknown`) das äußere Projekt Untertyp-Aggregators.

|Interface|Projektuntertyp|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Ermöglicht den Projektuntertyp an:<br /><br /> -Stellen Sie eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />: Ermöglicht den Projektuntertyp eine eigene Implementierung der Steuern des Start des Debuggers <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />– Deaktivieren Sie die ausdrucksauswertung zur Entwurfszeit durch angemessen behandelt die `DBGLAUNCH_DesignTimeExprEval` in seiner Implementierung von Groß-/Kleinschreibung <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Ermöglicht den Projektuntertyp an:<br /><br /> -Erweitern die <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> des Projekts, das Hinzufügen oder Entfernen von unabhängigen Konfigurationseigenschaften des Projekts.<br />– Erweitern Sie das Automation-Projektobjekt (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>) des Projekts.<br /><br /> Eigenschaftswerte, die oben genannten stammen aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Enumeration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Ermöglicht dem Projektuntertyp zurück zum Zuordnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekt, die dem projektkonfigurationssuchobjekt angegeben.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Ermöglicht dem Projektuntertyp zurück zum Zuordnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oder `VSITEMID` -Objekt, das projektkonfigurationssuchobjekt angegeben.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Ermöglicht den Projektuntertyp beliebige strukturierte XML-Daten in der Projektdatei (VBPROJ oder csproj) beibehalten werden. Diese Daten sind nicht für MSBuild sichtbar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Ermöglicht den Projektuntertyp an:<br /><br /> -Hinzufügen von neuen MSBuild-Eigenschaften beibehalten werden sollen.<br />-Entfernen Sie unnötige Eigenschaften von MSBuild.<br />-Abfrage für einen aktuellen Wert der MSBuild-Eigenschaft.<br />-Ändern Sie den aktuellen Wert der MSBuild-Eigenschaft.|

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>