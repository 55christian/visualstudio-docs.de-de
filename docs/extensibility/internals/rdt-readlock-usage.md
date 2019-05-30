---
title: RDT_ReadLock-Verwendung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c11cee4c1f8c150fc8bcf42b3dbc1a193d3441a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341355"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock-Verwendung

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) ist ein Flag, das Logik bereitstellt, für das Sperren eines Dokuments in der ausgeführten Dokumenttabelle (RDT), dies ist die Liste aller Dokumente, die derzeit in der Visual Studio-IDE geöffnet sind. Dieses Flag wird bestimmt, wenn Dokumente geöffnet sind, und gibt an, ob ein Dokument in der Benutzeroberfläche sichtbar oder unsichtbar im Arbeitsspeicher vorhandenen ist.

Im Allgemeinen verwenden Sie [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) Wenn eines der folgenden Bedingungen zutrifft:

- Öffnen Sie ein Dokument im Hintergrund werden sollen und Read-only, aber es ist noch nicht hergestellt, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> muss der Eigentümer.

- Sie möchten die Benutzer aufgefordert, ein Dokument zu speichern, die im Hintergrund geöffnet wurde, bevor der Benutzer sie in der Benutzeroberfläche angezeigt, und anschließend wurde versucht, ihn zu schließen.

## <a name="how-to-manage-visible-and-invisible-documents"></a>So verwalten Sie sichtbar und unsichtbar Dokumente

Wenn ein Benutzer ein Dokument in der Benutzeroberfläche öffnet eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Besitzer für das Dokument muss eingerichtet werden und ein [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) Flag festgelegt werden muss. Wenn kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Besitzer hergestellt werden kann, und klicken Sie dann das Dokument wird nicht gespeichert werden, wenn der Benutzer klickt **Alles speichern** oder die IDE geschlossen. Dies bedeutet, wenn ein Dokument geöffnet unsichtbar ist, wo er im Arbeitsspeicher geändert wird, und der Benutzer dazu aufgefordert werden, um das Dokument beim Herunterfahren speichern oder gespeichert, wenn **Alles speichern** ausgewählt wird, wird eine `RDT_ReadLock` kann nicht verwendet werden. Sie müssen stattdessen eine `RDT_EditLock` und registrieren Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> beim ein [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) Flag.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock und Änderung von Dokumenten

Das vorherige Flag erwähnt gibt an, dass das unsichtbare Öffnen des Dokuments führt seine `RDT_EditLock` beim Öffnen des Dokuments durch den Benutzer in ein sichtbares **DocumentWindow**. In diesem Fall erhält der Benutzer mit einer **speichern** aufgefordert, wenn die sichtbaren **DocumentWindow** geschlossen wird. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` Implementierungen, mit denen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> Dienst anfänglich arbeiten, wenn nur ein `RDT_ReadLock` stammt (d. h., wenn das Dokument im Hintergrund geöffnet wird, um Informationen zu analysiert). Später, wenn das Dokument geändert werden muss, klicken Sie dann die Sperre wird aktualisiert, eine schwache **RDT_EditLock**. Wenn der Benutzer klicken Sie dann das Dokument in ein sichtbares öffnet **DocumentWindow**, `CodeModel`des schwachen `RDT_EditLock` veröffentlicht wird.

Wenn der Benutzer dann schließt der **DocumentWindow** und wählt **keine** bei der Aufforderung zum Speichern Sie des geöffneten Dokuments, das `CodeModel` Implementierung verwirft alle Informationen im Dokument und erneut öffnet die Dokument vom Datenträger unsichtbar das nächste Mal, das Informationen für das Dokument erforderlich ist. Die Besonderheit dieses Verhalten ist eine Instanz, in denen der Benutzer öffnet, die **DocumentWindow** des unsichtbar geöffneten Dokuments, ändert, wird geschlossen und wählt dann **keine** bei der Aufforderung zum Speichern des Dokuments. In diesem Fall, wenn das Dokument besitzt eine `RDT_ReadLock`, klicken Sie dann das Dokument wird nicht geschlossen werden, und das geänderte Dokument bleibt unsichtbar im Arbeitsspeicher, geöffnet, auch wenn der Benutzer hat nicht das Dokument zu speichern.

Wenn das unsichtbare Öffnen des Dokuments eine schwache verwendet `RDT_EditLock`, und er stellt eine Sperre, wenn der Benutzer das Dokument sichtbar öffnet und keine anderen Sperren aufrechterhalten werden. Wenn der Benutzer schließt die **DocumentWindow** und wählt **keine** wenn dazu aufgefordert werden, um das Dokument speichern, klicken Sie dann das Dokument muss geschlossen werden, aus dem Arbeitsspeicher. Dies bedeutet, dass der Client nicht sichtbare für RDT-Ereignisse zum Nachverfolgen der dieses Ereignis überwachen muss. Das nächste Mal das Dokument erforderlich ist, muss das Dokument erneut geöffnet werden.