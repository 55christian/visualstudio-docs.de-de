---
title: Console | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e947fb28c92323f0d4d66c697c272699fc63450e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771055"
---
# <a name="console"></a>Konsole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPerfCmd.exe-Option **Console** startet die angegebene Anwendung in einem neuen Eingabeaufforderungsfenster. **Console** kann nur mit der VSPerfCmd-Option **Launch** verwendet werden. Wenn die Anwendung keine Befehlszeilenanwendung ist, hat **Console** keine Auswirkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="required-options"></a>Erforderliche Optionen  
 **Console** kann nur in einer Befehlszeile angegeben werden, die auch die Option **Launch** enthält.  
  
 **Starten:** `AppName`  
 Startet den Profiler und die von `AppName` festgelegten Anwendungen.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
