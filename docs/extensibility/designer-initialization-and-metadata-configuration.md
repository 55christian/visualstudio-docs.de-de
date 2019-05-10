---
title: Designer-Initialisierung und Metadatenkonfiguration | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ed1852780e8045f298ed30f10ace5d971776294
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864084"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Designer-Initialisierung und die Metadaten-Konfiguration

Bearbeitung von einem Designer oder Designerkomponente zugeordneten Metadaten und Filter Attribute bietet einen Mechanismus für Anwendungen definieren, welche Tools von einem bestimmten Designer verwendet werden, um andere zu behandeln <xref:System.Type> Objekte (z. B. Datenstrukturen Klassen oder grafische Entitäten), wenn der Designer verfügbar ist, und wie die vom Designer unterstützt für Visual Studio-IDE konfiguriert ist (für die Instanz die **Toolbox** -Kategorie oder-Registerkarte zur Verfügung steht).

Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet verschiedene Mechanismen, um das Steuerelement eine des Designers oder des Designerkomponente Initialisierung und die Bearbeitung seiner Metadaten von einem VSPackage zu erleichtern.

## <a name="initialize-metadata-and-configuration-information"></a>Initialisieren von Metadaten und Konfiguration
 Da sie bei Bedarf geladen werden, VSPackages möglicherweise nicht von der Visual Studio-Umgebung vor der Instanziierung eines Designers geladen wurden. Aus diesem Grund VSPackages können keine den Standardmechanismus für die Konfiguration von einem Designer oder Designer-Komponente auf erstellen, über die behandeln eine <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Ereignis. Eine VSPackage implementiert stattdessen eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Schnittstelle, und registriert sich selbst zum Bereitstellen von Anpassungen, die als "Design Surface-Erweiterungen" bezeichnet.

### <a name="customize-initialization"></a>Anpassen von Initialisierung

Anpassen von einem Designer, einer Komponente oder ein Designer-Oberfläche umfasst:

1. Ändern die Designer-Metadaten und effektiv ändern, wie eine bestimmte <xref:System.Type> zugegriffen oder konvertiert wird.

    Dies erfolgt normalerweise über die <xref:System.Drawing.Design.UITypeEditor> oder <xref:System.ComponentModel.TypeConverter> Mechanismen.

    Z. B. wenn <xref:System.Windows.Forms>-Basis-Designer initialisiert werden, ändert Visual Studio-Umgebung die <xref:System.Drawing.Design.UITypeEditor> für <xref:System.Web.UI.WebControls.Image> Objekte, die mit dem Designer verwendet, um die Ressourcen-Manager verwenden, um Bitmaps anstatt im Dateisystem zu erhalten.

2. Integrieren mit der Umgebung, z. B. durch Abonnieren von Ereignissen oder Abrufen der Konfigurationsinformationen des Projekts. Abrufen von Projektkonfigurationsinformationen und Abonnieren von Ereignissen durch Abrufen der <xref:System.ComponentModel.Design.ITypeResolutionService> Schnittstelle.

3. Änderung der benutzerumgebung durch Aktivieren der entsprechenden **Toolbox** Kategorien oder Beschränken des Designers Anwendbarkeit durch Anwenden einer Instanz von der <xref:System.ComponentModel.ToolboxItemFilterAttribute> Klasse, um den Designer.

### <a name="designer-initialization-by-a-vspackage"></a>Designer-Initialisierung von einem VSPackage

Eine VSPackage sollte das Designer-Initialisierung von verarbeiten:

1. Erstellen ein Objekt, das die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse.

   > [!NOTE]
   > Die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse sollte nie implementiert werden, auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.Shell.Package> Klasse.

2. Registrieren die Klasse, die implementiert <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> als bieten Unterstützung für die VSPackage Designer-Erweiterungen. Registrieren Sie die Klasse durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>, und <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf die Klasse, die die VSPackage Implementierung bietet <xref:Microsoft.VisualStudio.Shell.Package>.

Wenn ein Designer oder ein Designer-Komponente erstellt wird, die Visual Studio-Umgebung:

- Greift auf jeden registrierten Entwurf entwurfsoberflächenerweiterungs-Anbieter.

- Instanziiert und initialisiert eine Instanz jedes Design entwurfsoberflächenerweiterungs-Anbieters <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt.

- Jeder Entwurf entwurfsoberflächenerweiterungs-Anbieter aufruft <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> Methode oder <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> -Methode (nach Bedarf).

Bei der Implementierung der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt als Member von einem VSPackage, es ist wichtig zu verstehen, dass:

- Visual Studio-Umgebung bietet keine Kontrolle über welche Metadaten oder sonstige Konfigurationseinstellungen ein bestimmtes `DesignSurfaceExtension` des Anbieters ändert. Es ist möglich, dass zwei oder mehr `DesignSurfaceExtension` Anbieter, die in Konflikt stehenden Möglichkeiten, mit der letzten Änderung, die definitive wird die gleiche Webdesigner-Feature ändern. Es ist unbestimmt, denen Änderungsfunktionen zuletzt angewendet wird.

- Es ist möglich, explizit eine Implementierung von beschränken die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt, das bestimmte Designer durch Anwenden von Instanzen von <xref:System.ComponentModel.ToolboxItemFilterAttribute> an, dass diese Implementierung. Weitere Informationen zu **Toolbox** Element filtern, finden Sie unter den <xref:System.ComponentModel.ToolboxItemFilterAttribute> und <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Zusätzliche Metadaten bereitstellen

Eine VSPackage kann es sich um die Konfiguration von einem Designer oder Designerkomponente außer zur Entwurfszeit ändern.

Die <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse angewendet, die zu einem VSPackage, das einen Designer bereitstellt oder programmgesteuert verwendet werden kann.

Eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse wird verwendet, um die Metadaten erstellt, die auf einer Entwurfsoberfläche Komponenten zu ändern. Eine konnte ersetzen Sie z. B. einen standardmäßigen-Eigenschaftenbrowser von verwendet <xref:System.Windows.Forms.CommonDialog> Objekte mit einem benutzerdefinierten Eigenschaftenbrowser.

Änderungen, die von einer Instanz von bereitgestellten <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> angewendet werden, um ein VSPackage Implementierung der <xref:Microsoft.VisualStudio.Shell.Package> kann einen der beiden Bereiche aufweisen:

- Global – für alle neuen Instanzen einer bestimmten Komponente

- Lokal, bezieht sich nur auf die Instanz der Komponente erstellt, die auf einer Entwurfsoberfläche, die vom aktuellen VSPackage bereitgestellt.

Die `IsGlobal` Eigenschaft der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Instanz angewendet wird, um ein VSPackage Implementierung der <xref:Microsoft.VisualStudio.Shell.Package> bestimmt dieser Bereich.

Anwenden des Attributs auf eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Package> mit der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> -Objekts festgelegt, um `true`, wie folgt, ändert sich den Browser für die gesamte Visual Studio-Umgebung:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Wenn das globale Flag, um festgelegt wurde `false`, und klicken Sie dann die Änderung der Metadaten für den aktuellen Designer unterstützt durch das aktuelle VSPackage lokal ist:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Die Entwurfsoberfläche unterstützt nur das Erstellen von Komponenten können, und daher nur die Komponenten lokalen Metadaten. Im obigen Beispiel, wir haben versucht, eine Eigenschaft zu ändern, wie z.B. die `Color` Eigenschaft eines Objekts. Wenn `false` für das globale Flag übergebene `CustomBrowser` würde nie angezeigt werden, da der Designer nie eine Instanz erstellt `Color`. Wenn auf das globale Flag `false` eignet sich für Komponenten, z. B. Steuerelemente, Timer und Dialogfelder.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Erweitern der entwurfszeitunterstützung](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)