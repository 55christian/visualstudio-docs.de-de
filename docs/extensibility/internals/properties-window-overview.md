---
title: Übersicht über das Eigenschaftenfenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05c772365c42037bfd97a2a31b80efc2f5f1a48b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347812"
---
# <a name="properties-window-overview"></a>Übersicht über Eigenschaftenfenster
Die **Eigenschaften** Fenster wird verwendet, um die Anzeigeeigenschaften für Objekte, die in der zwei Haupttypen von Windows verfügbar in ausgewählten der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Diese beiden Arten von Windows sind:

- Toolfenster, z. B. den Projektmappen-Explorer, Klassenansicht und Objekt-browser

- Dokumentfenster mit, wie Editoren und Designern die Forms-Designer-Editor für XML und HTML-editor

## <a name="using-the-properties-window"></a>Mithilfe des Eigenschaftenfensters
 Die **Eigenschaften** Fenster zeigt die Eigenschaften der einzelnen oder mehrerer ausgewählter Elemente. Wenn mehrere Elemente ausgewählt sind, wird die Schnittmenge aller Eigenschaften für alle ausgewählten Objekte angezeigt.

 Ereignisse im Zusammenhang mit einem ausgewählten Objekt in einem Formular-Designer-Fenster oder eine HTML-Editor mit COM+-Metadaten werden angezeigt, der **Eigenschaften** Fenster. Sie können z. B. eine Schaltfläche auswählen und zeigt die zugeordneten Ereignisse, z. B. eine `OnClick` -Ereignis, das auf diese Schaltfläche verknüpft werden kann.

 Ereignisse, die angezeigt wird, der **Eigenschaften** Fenster dienen in erster Linie mit Objekten, die an Code gebunden sind. Wenn Sie ein Dateiformat, die nicht etwas mit Code zu tun bearbeiten, möchten Sie keine Ereignisse haben. Ereignisse werden nur angezeigt, der **Eigenschaften** anzeigen, wenn eine Bindung zwischen der Ausführung von Code und bestimmte Ereignisse im Zusammenhang mit spezifischen Objekten vorhanden ist. Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt, das ausgeführt wird, wenn das Objekt aktiviert wird.

 Die folgende Tabelle enthält die primären Schnittstellen, die von der **Eigenschaften** Fenster.

|Schnittstellenname|Beschreibung|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Enthält eine Liste der Kategorien für die **Eigenschaften** Fenster und ordnet jede Eigenschaft zu einer Kategorie.|
|[IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Macht Methoden und Eigenschaften für die Programmierung von Tools und andere Anwendungen, die Unterstützung der Automatisierung des Objekts.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Stellt mit den Auslassungspunkten (...)-Schaltflächen namens *Generatoren* öffnen, die Sie modalen Dialogfeldern, die durch das Objekt selbst implementiert. Verwendet, wenn ein Wert vom Benutzer in einem Textfeld einfach nicht typisiert ist. Beispielsweise kann verwendet werden, um ein Farbwähler zu öffnen, der den RGB-Wert für Sie bestimmt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Bietet Zugriff auf Objekte, die zum Aktualisieren von Informationen in den **Eigenschaften** Fenster. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster implementiert, auswählbaren Objekte mit verwandten Eigenschaften, die angezeigt werden enthält.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Enthält Informationen zu den Typ eines Objekts, z. B. Methoden einer Schnittstelle und Felder einer Struktur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Ermöglicht VSPackages Auswahlereignisse zu empfangen und Informationen über die aktuelle Projekthierarchie, Element, Elementwert und den befehlsbenutzeroberflächenkontext abzurufen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt die Umgebung mit Zugriff auf die Mehrfachauswahl bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Zur Bereitstellung von lokalisierter Namen für einige Eigenschaften angezeigt, der **Eigenschaften** Fenster.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Benachrichtigt registrierte VSPackages über Änderungen an der aktuellen Auswahl, der Wert des Elements oder der befehlsbenutzeroberflächenkontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Benachrichtigt die Umgebung über eine Änderung in der aktuellen Auswahl, und ermöglicht den Zugriff auf die Hierarchie und Element-Informationen, die im Zusammenhang mit der neuen Auswahl.|

 Weitere Informationen zu `IDispatch`, finden Sie unter der MSDN Library.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
- [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)