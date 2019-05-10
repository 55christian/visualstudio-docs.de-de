---
title: VSTextBuffer-Objekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 950f9c50ccaf137b21d775ceaf1bff196b1b8ac7
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "59001113"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer-Objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der TextBuffer-Objekt stellt einen Stream von Unicode-Text, der in der Regel von einer Datei zugeordnet ist. Ein <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt kann außerhalb des Kontexts der Kern-Editor, wie im Fall eines Assistenten verwendet werden.  
  
 Die folgende Tabelle zeigt die Schnittstellen der `VSTextBuffer`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standard-OLE-Schnittstelle. Vor allem verwendet für Rückgängigmachen/Wiederholen-Behandlung im Puffer.|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standard-OLE-Schnittstelle.|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Aktionen für zusammengesetzte Wörter (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz der Dokumentdaten, die vom Textpuffer verwaltet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt die grundlegenden Dienste. wird von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Suchen einen Puffer verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese- / Schreibzugriff mithilfe der zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese- / Schreibzugriff mithilfe der eindimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Ermöglicht schnelle und Stream-ausgerichteten sequenziellen Zugriff auf Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Sie können Ihre eigenen zufällige Daten in den Puffer mit dieser Schnittstelle speichern, indem erstellen eine GUID und diese als Schlüssel verwenden.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|  
  
## <a name="remarks"></a>Hinweise  
 Die `VSTextBuffer` befindet sich in der Regel durch einen `QueryInterface` Aufrufen `IVsTextBuffer`. Weitere Informationen finden Sie unter [Textpuffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Abbildungen bearbeiten](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
