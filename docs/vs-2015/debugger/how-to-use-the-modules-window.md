---
title: 'Vorgehensweise: Verwenden des Modulfensters | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
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
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b19237b94ed3d53c49f248e22b86d3af8180625
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445050"
---
# <a name="how-to-use-the-modules-window"></a>Vorgehensweise: Verwenden des Modulfensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Diese Funktion ist für das SQL-Debuggen nicht verfügbar.  
  
 Die **Module** DLLs und EXE-Datei, die von Ihrem Programm verwendet werden, und zeigt relevante Informationen für jedes Fenster aufgelistet.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>So zeigen Sie das Fenster Module im Unterbrechungsmodus oder Ausführungsmodus an  
  
- Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie dann auf **Module**.  
  
     Module werden im Fenster **Module** standardmäßig nach der Ladereihenfolge sortiert. Sie können sie jedoch nach einer beliebigen Spalte sortieren.  
  
### <a name="to-sort-by-any-column"></a>So sortieren Sie nach einer beliebigen Spalte  
  
- Klicken Sie auf die Schaltfläche am oberen Rand der Spalte.  
  
     Sie können Symbole laden oder einen Symbolpfad angeben der **Module** Fenster über das Kontextmenü.  
  
## <a name="loading-symbols"></a>Laden von Symbolen  
 In der **Module** Fenster können Sie sehen, welche Module Debugsymbole geladen. Diese Informationen angezeigt, der **Symbolstatus** Spalte. Lautet der Status **übersprungen LoadingCannot finden oder öffnen Sie die PDB-Datei**, oder **laden, die von der Einstellung zum Einschließen/Ausschließen deaktiviert**, können Sie den Debugger, um Symbole von den öffentlichen Microsoft-Symboldateien herunterzuladen leiten Server oder zum Laden der Symbole aus einem Symbolverzeichnis auf Ihrem Computer. Weitere Informationen finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>So laden Sie Symbole manuell  
  
1. In der **Module** Fenster mit der rechten Maustaste ein Modul, die für den keine Symbole geladen wurden.  
  
2. Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbolserver** oder **Symbolpfad**.  
  
#### <a name="to-change-symbol-load-settings"></a>So ändern Sie Einstellungen zum Laden von Symbolen  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein beliebiges Modul.  
  
2. Klicken Sie auf **Symboleinstellungen**.  
  
     Sie können jetzt die Symbol-laden-Einstellungen ändern, wie in beschrieben [angeben der symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf das Modul.  
  
2. Zeigen Sie auf **automatische Symboleinstellungen laden** , und klicken Sie dann auf **immer manuell laden** oder **Standard**. Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterbrechen der Ausführung](http://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
