---
title: VSTextView-Objekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eddd5640b2f8f073f791f6bdb4dc006f8fab0e36
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322812"
---
# <a name="vstextview-object"></a>VSTextView-Objekt
Die Textansicht ist ein Fenster, das ermöglicht Benutzern das Anzeigen und bearbeiten den Unicode-Text des Textpuffers. Im Wesentlichen ist die Ansicht, was die meisten Benutzer als Editor bezeichnet. Da die Ansicht aus dem Puffer von verschiedenen Textebenen (Zeilenumbruch, Gliederung, Text usw.) getrennt ist, wird die Sicht nicht garantiert eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht, finden Sie unter [zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 Die folgende Tabelle zeigt die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

|Interface|Beschreibung|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von verbundaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegende Methoden für die Verwaltung und den Zugriff auf die Ansicht bereit. `IVsTextView` ist nicht sicher Thread.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interaktion mit Textebenen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Sicht von einem anderen Thread.|

## <a name="see-also"></a>Siehe auch
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)
- [Zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)