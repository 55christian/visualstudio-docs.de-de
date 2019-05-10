---
title: PF | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf6bc8ae841ad8ba0d3fd376176bdff2332fb958
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432006"
---
# <a name="pf"></a>PF
Die *VSPerfCmd.exe*-Option **PF** legt das Profilerstellungsereignis fest, das auf Seitenfehler gesampelt wird, und ändert optional die Anzahl der Zyklen in einem Samplingintervall vom Standard 10 auf einen anderen Wert.

> [!NOTE]
> **PF** kann nicht in 64-Bit-Systemen verwendet werden.

**PF** kann nur in einer Befehlszeile verwendet werden, die auch die Optionen **Launch** (Starten) und **Attach** (Anfügen) enthält.

 Standardmäßig ist das Samplingereignis auf angehaltene Prozessortaktzyklen festgelegt und das Samplingintervall auf 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.

 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** oder **Attach** enthält.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parameter
 `Events`: ist ein ganzzahliger Wert, der die Anzahl der Seitenfehlerereignisse in einem Samplingintervall angibt. Wenn `Events` nicht festgelegt wurde, wird das Intervall auf 10 festgelegt.

## <a name="required-options"></a>Erforderliche Optionen
 **PF** kann nur in einer Befehlszeile festgelegt werden, die eine der folgenden Optionen enthält.

 **Launch:** `AppName` startet den Profiler und die von AppName festgelegten Anwendungen.

 **Attach:** `PID` fügt den Profiler an den von AppName angegebenen Prozess an.

## <a name="invalid-options"></a>Ungültige Optionen
 Die folgenden Optionen können nicht in derselben Befehlszeile wie **PF** angegeben werden.

 **Timer**[**:**`Cycles`]: legt das Samplingereignis auf die Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest. Das Timer-Standardintervall beträgt 10.000.000.

 **Sys**[**:**`Events`]: legt das Samplingereignis auf Aufrufe von der Anwendung mit Profil auf den Betriebssystemkernel (syscalls) und das Samplingintervall optional auf `Events` fest. Das standardmäßige Sys-Intervall beträgt 10.

 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]: legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator und das Samplingintervall auf `Reload` fest.

 **GC**[**:**{**Allocation**&#124;**Lifetime**}]: erfasst .NET-Arbeitsspeicherdaten. Wenn der Parameter **Allocation** angegeben wird (Standard), werden Daten bei jedem Speicherbelegungsereignis gesammelt. Wenn jedoch der **Lifetime**-Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection-Ereignis gesammelt.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird veranschaulicht, wie das Profilerstellungs-Samplingereignis auf Seitenfehler festgelegt und das Samplingintervall auf 20 Seitenfehler festgelegt wird.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)