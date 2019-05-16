---
title: Hostprozess (vshost.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 43feac58c024c0eda8b8930fba05c0c92f7ac6bd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704319"
---
# <a name="hosting-process-vshostexe"></a>Hostprozess (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Hostprozess verbessert die Debugleistung und ermöglicht das Debuggen von teilweise vertrauenswürdigen Anwendungen und die Ausdrucksauswertung zur Entwurfszeit. Die Hostprozessdateien enthalten vshost im Dateinamen und befinden sich im Ausgabeordner Ihres Projekts. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
> Hostprozessdateien (.vshost.exe) sind für die Verwendung von Visual Studio und sollten nicht direkt ausgeführt oder mit Ihrer Anwendung bereitgestellt werden.  
  
## <a name="improved-debugging-performance"></a>Verbesserte Debugleistung  
 Der Hostprozess erstellt eine Anwendungsdomäne und ordnet die Anwendung dem Debugger zu. Das Ausführen dieser Aufgaben kann zu einer spürbaren Verzögerung zwischen der Zeit, wenn das Debuggen gestartet wird, und der Zeit, wenn die Anwendung beginnt, führen. Der Hostprozess hilft die Leistung durch das Erstellen der Anwendungsdomäne und das Zuordnen des Debuggers im Hintergrund zu steigern sowie durch Speichern der Anwendungsdomäne und des Debuggerzustands zwischen den Ausführungen der Anwendung. Weitere Informationen zu Anwendungsdomänen finden Sie unter [Anwendungsdomänen](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Das Debuggen teilweise vertrauenswürdiger Anwendungen  
 Eine Anwendung kann auf der [Seite „Sicherheit“](../ide/reference/security-page-project-designer.md) vom **Projekt-Designer** als teilweise vertrauenswürdige Anwendung angegeben werden. Das Debuggen einer teilweise vertrauenswürdigen Anwendung erfordert spezielle Initialisierung der Anwendungsdomäne. Diese Initialisierung erfolgt über den Hostprozess.  
  
## <a name="design-time-expression-evaluation"></a>Ausdrucksauswertung zur Entwurfszeit  
 Die Ausdrucksauswertung zur Entwurfszeit können Sie zum Testen von Code aus dem **direkten** Fenster verwenden, ohne die Anwendung auszuführen. Der Hostprozess führt diesen Code während der Ausdrucksauswertung zur Entwurfszeit aus. Weitere Informationen finden Sie unter [Direktfenster](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
 [Vorgehensweise: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md)   
 [Direktfenster](../ide/reference/immediate-window.md)   
 [Anwendungsdomänen](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
