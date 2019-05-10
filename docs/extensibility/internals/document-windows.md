---
title: Dokumentieren von Windows | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 490c39b9e97ad6a55ca2d1695d31b85ecc13dc57
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418595"
---
# <a name="document-windows"></a>Dokumentfenster
In Visual Studio eine *Dokumentfenster* ist ein gerahmter untergeordnete Fenster, das ein Fenster für die Multiple Document Interface (MDI) zugeordnet ist. Dokumentfenster in der Regel für die Anzeige und Änderung von Quellcode oder Text verwendet werden, aber sie können auch andere funktionale Typen hosten. Dokumentfenster:

- Können in separaten horizontale oder vertikale Registerkartengruppen in der übergeordneten MDI organisiert werden, sodass mehrere Dateien gleichzeitig angezeigt werden können.

- Können in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.

- Kostenlos abgedockt werden können.

- In der Aktivierreihenfolge auf andere MDI-Fenster sind verknüpft werden.

  Die Befehle für die Gruppierung, können auf der rechten Maustaste auf eine Fensterregisterkarte Dokument andockbare und unverankerte gefunden werden.

  Weitere Informationen zu Verhalten in Visual Studio, finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Dokumentfensterimplementierung
 Dokumentfenster werden erstellt, durch die Implementierung eines Editors. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> -Schnittstelle erstellt Dokumentfenster im Rahmen der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy-Schnittstellen im Editor](../../extensibility/legacy-interfaces-in-the-editor.md).

> [!NOTE]
> Rückwärts und navigationspunkte in einem Fenster weiterzuleiten, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle. Text-Editor wird Textmarkierungen navigationspunkte im Dokument identifiziert.

## <a name="the-running-document-table"></a>Die aktive Dokumenttabelle
 Die IDE verwendet die aktive Dokumenttabelle (RDT), um den Status jedes Dokumentfenster nachzuverfolgen. Der RDT ist der Mechanismus, über welches, den Dokument Windows benachrichtigt werden, Ereignisse, z. B. wenn eine Projektmappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Document-Tabelle mit](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Siehe auch
- [Verzögertes Laden von Dokumenten](../../extensibility/internals/delayed-document-loading.md)