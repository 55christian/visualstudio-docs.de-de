---
title: Attach | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b9adb5a0a47c1ee98e0e390cfaf8b3a6dc78146
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433792"
---
# <a name="attach"></a>Anfügen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPerfCmd.exe-Option **Attach** beginnt die Samplingprofilerstellung für den laufenden Prozess, der von der Prozess-ID (PID) angegeben wird.  
  
 Um **Attach** zu verwenden, müssen Sie die Methode **Sample** in der Option „Start“ angeben.  
  
> [!NOTE]
> Wenn die Option **CrossSession** für die Option **Start** angegeben wurde, müssen alle Aufrufe von **VSPerfCmd /Attach** oder **VSPerfCmd /Detach** auch **CrossSession** angeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `ProcessID`  
 Die Prozess-ID (PID) des laufenden Prozesses. Die PID eines laufenden Prozesses wird auf der Registerkarte „Prozesse“ des Windows Task-Managers aufgeführt.  
  
## <a name="valid-options"></a>Gültige Optionen  
 Die folgenden **VSPerfCmd**-Optionen können mit der Option **Attach** in derselben Befehlszeile kombiniert werden.  
  
 **CrossSession**  
 Aktiviert die Profilerstellung für Anwendungen in Sitzungen, die keine Anmeldesitzungen sind. Diese Option ist erforderlich, wenn die Option **Start** mit der Option **CrossSession** angegeben wurde.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen-Profilersitzung und legt die angegebene Profilerstellungsmethode fest  
  
 **TargetCLR**  
 Gibt die Version der .NET Framework-CLR (Common Language Runtime) für die Profilerstellung an, wenn mehr als eine Version in einer Profilerstellungssitzung geladen wird. Standardmäßig wird für die zuerst geladene Version ein Profil erstellt.  
  
 **GlobalOn GlobalOff**  
 Setzt die Profilerstellung fort (**GlobalOn**) oder unterbricht sie (**GlobalOff**), aber nicht die Profilerstellungssitzung  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Setzt die Profilerstellung für den angegebenen Prozess fort (**ProcessOn**) oder unterbricht sie (**ProcessOff**)  
  
## <a name="interval-options"></a>Intervalloptionen  
 Eine der folgenden Optionen für Samplingintervalle kann in der Attach-Befehlszeile angegeben werden. Das Standardsamplingintervall sind 10.000.000 Prozessortaktzyklen.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong>Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]  
 Gibt die Anzahl und den Typ des Samplingintervalls an  
  
- **Timer**: Sampelt alle `Cycles`-Prozessortaktzyklen. Wenn `Cycles` nicht angegeben ist, wird ein Intervall von 10.000.000 verwendet.  
  
- **PF**: Sampelt alle `Events`-Seitenfehler. Wenn `Events` nicht angegeben ist, geschieht dies bei jedem 10. Seitenfehler.  
  
- **Sys**: Sampelt `Events`-Aufrufe des Betriebssystems. Wenn `Events` nicht angegeben ist, wird jeder 10. Systemaufruf untersucht.  
  
- **Counter**: Sampelt alle `Reload`-Zahlen der von `Name` angegebenen CPU-Leistungsindikatoren. `FriendlyName` kann optional eine Zeichenfolge angeben, die als Spaltenüberschrift in Profilerberichten verwendet wird.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird veranschaulicht, wie eine ausgeführte Instanz einer Anwendung mit der Prozess-ID 12345 angefügt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
