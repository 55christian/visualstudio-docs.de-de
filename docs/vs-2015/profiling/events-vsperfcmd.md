---
title: Events (VSPerfCmd) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 265dc7f84fbd1ec19b520e2e30d3554e2c66683b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302135"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPerfCmd.exe-Option **Events** steuert die Protokollierung der Ereignisablaufverfolgung für Windows (ETW). ETW-Daten werden in einer ETL-Datei gespeichert, die von der Profiler-Datendatei getrennt ist. Die Daten können in einem Bericht mithilfe des Befehls „[VSPerfReport ](../profiling/vsperfreport.md) /summary: etw“ angezeigt werden.  
  
 Die Option **Events** kann jederzeit aufgerufen werden, bevor der VSPerfCmd-Befehl **Shutdown** zum Beenden der Profilerstellung aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parameter  
 **On**|**Off**  
 Startet oder beendet die Sammlung von Ereignisdaten  
  
 `Guid`  
 Die GUID des Anbietersteuerelements  
  
 `ProviderName`  
 Der Name des Anbieters, der bei der Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) registriert ist  
  
 `Flags`  
 Ein mit „0x“ präfigierter Wert eines hexadezimal Flags, der vom Ereignisanbieter definiert wird  
  
 `Level`  
 Gibt die Menge der gesammelten Daten an. `Level` wird vom Ereignisanbieter definiert.  
  
 Die Option **Events** versteht die folgenden Kernelschlüsselwörter als Anbieternamen:  
  
 **Process**  
 Prozessereignisse  
  
 **Thread**  
 Threadereignisse  
  
 **Image**  
 Lade- und Entladeereignisse für Bilder  
  
 **Disk**  
 E/A-Datenträgerereignisse  
  
 **Datei**  
 E/A-Dateiereignisse  
  
 **Hardfault**  
 Harte Seitenfehler  
  
 **Pagefault**  
 Weiche Seitenfehler  
  
 **Network**  
 Netzwerkereignisse  
  
 **Registry**  
 Ereignisse beim Zugriff auf die Registrierung  
  
 Beachten Sie, dass der Kernelanbieter nur aktiviert werden kann. Er kann weder deaktiviert werden, noch können Flags geändert werden, bis der Monitor heruntergefahren wurde.  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
> Wenn CLR-ETW-Ereignisse aktiviert sind, werden im Bericht in der Ablaufverfolgungsansicht auch zusätzliche Startdaten gesammelt. Mit dem folgenden Befehl vermeiden Sie, dass Startereignisse im Bericht angezeigt werden:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Wenn Sie Startereignisse nicht ausschließen, werden sie als GUIDs im Bericht angezeigt, weil sie nicht in der MOF-Datei (Managed Object Format) aufgeführt werden. Weitere Informationen finden Sie auf dieser Microsoft-Website: [Sample Managed Object Format (MOF) File (Managed Object Format-Beispieldatei (MOF))](https://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiling Stand-Alone Applications (Profilerstellung für eigenständige Anwendungen)](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
