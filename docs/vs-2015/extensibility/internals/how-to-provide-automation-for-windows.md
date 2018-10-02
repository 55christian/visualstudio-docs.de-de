---
title: 'Vorgehensweise: Bereitstellen von Automatisierung für Windows | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fad49e2841186cea677a165bdb48c4a1af5b41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515075"
---
# <a name="how-to-provide-automation-for-windows"></a>Vorgehensweise: Bereitstellen von Automatisierung für Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Bereitstellen von Automatisierung für Windows](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-automation-for-windows).  
  
Sie können Automation für die Dokument- und-Toolfenster bereitstellen. Bietet Automation empfiehlt sich, wenn Sie Automatisierungsobjekte in einem Fenster verfügbar machen möchten, und die Umgebung noch nicht bieten Sie eine vorgefertigte Automatisierungsobjekt, wie mit einer Aufgabenliste.  
  
## <a name="automation-for-tool-windows"></a>Automatisierung für das Tool Windows  
 Die Umgebung ermöglicht eine Automatisierung durch Zurückgeben von Standard in einem Toolfenster <xref:EnvDTE.Window> Objekt wie im folgenden Verfahren beschrieben:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Bereitstellen von Automatisierung für Toolfenster  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode über die Umgebung mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> als `VSFPROPID` Parameter, um die `Window` Objekt.  
  
2.  Wenn ein Aufrufer eine VSPackage-spezifisches Automatisierungsobjekt für das Toolfenster über anfordert <xref:EnvDTE.Window.Object%2A>, die Umgebung ruft `QueryInterface` für `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, oder die `IDispatch` Schnittstellen. Beide `IExtensibleObject` und `IVsExtensibleObject` bieten eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> Methode.  
  
3.  Wenn die Umgebung anschließend ruft der `GetAutomationObject` -Methode und übergeben Sie `NULL`, reagieren, indem Sie übergeben sichern Ihre VSPackage-Objekt.  
  
4.  Wenn der Aufruf `QueryInterface` für `IExtensibleObject` und `IVsExtensibleObject` ein Fehler auftritt, und klicken Sie dann die Umgebung ruft `QueryInterface` für `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatisierung für das Dokument Windows  
 Ein Standard <xref:EnvDTE.Document> Objekt steht auch über die Umgebung, auch ein Editor eine eigene Implementierung von verfügen, kann die `T:EnvDTE.Document` Objekt durch die Implementierung `IExtensibleObject` -Schnittstelle von und reagieren auf `GetAutomationObject`.  
  
 Darüber hinaus bieten ein Editor ein VSPackage-spezifisches Automatisierungsobjekt, abrufen, der über die <xref:EnvDTE.Document.Object%2A> Methode, durch die Implementierung der `IVsExtensibleObject` oder `IExtensibleObject` Schnittstellen. Die [VSSDK-Beispiele](../../misc/vssdk-samples.md) ein RTF-Automatisierungsobjekt dokumentspezifische beiträgt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
