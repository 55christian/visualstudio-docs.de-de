---
title: 'Vorgehensweise: Verwenden einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446435"
---
# <a name="how-to-use-a-visualizer"></a>Vorgehensweise: Verwenden einer Schnellansicht
Sie können den Inhalt einer Variable oder eines Objekts mithilfe einer Schnellansicht in einer für den Datentyp sinnvollen Art anzeigen. Können Schnellansichten über **DataTips**, **Überwachen** Fenster die **"Auto"** Fenster oder die **"lokal"** Fenster.  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
> In **Store** apps, die nur den Standardtext, HTML, XML und JSON-Schnellansichten werden unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
### <a name="to-open-a-visualizer"></a>So öffnen Sie eine Schnellansicht  
  
1. Klicken Sie auf das Lupensymbol neben einem Variablennamen in **DataTips**, **Watch** Fenster oder in der **"Auto"**, **"lokal"**, oder **Schnellansicht** Fenster.  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2. Klicken Sie auf die gewünschte Schnellansicht.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>So verwenden Sie eine Schnellansicht für verwalteten Code während des Remotedebuggens  
  
- Kopieren Sie die Schnellansicht-DLL auf den Remotecomputer, bevor Sie die Debugsitzung starten.  
  
     Der Pfad zur DLL muss auf dem Remotecomputer und dem lokalen Computer derselbe sein. Dieser Pfad kann einer der folgenden Speicherorte sein:  
  
     *Visual Studio-Installationspfad* `\Common7\Packages\Debugger\Visualizers`  
  
     - oder -   
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio Version* `\Visualizers`  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Vorgehensweise: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)   
 [Anzeigen von Datenwerten als Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)