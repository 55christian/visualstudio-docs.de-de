---
title: Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e71f1d8219f61946bc8242514429130530fb12
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440248"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Sammeln von Anwendungsstatistiken für Dienste mithilfe der Profiler-Samplingmethode
In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsstatistiken für Windows-Dienste mithilfe der Samplingmethode über die Befehlszeile beschrieben.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Anfügen des Profilers an einen .NET-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Hinzufügen von Ebeneninteraktionsdaten**|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Anfügen des Profilers an einen C/C++-Dienst**|-   [Vorgehensweise: Anfügen des Profilers an einen nativen Dienst zum Sammeln von Anwendungsstatistiken](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

### <a name="profile-windows-services"></a>Profilerstellung für Windows-Dienste

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung mit der Instrumentationsmethode**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profilerstellung der .NET-Speicherbelegung und Garbage Collection**|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profilerstellung mit der Samplingmethode

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilerstellung für ASP.NET-Webanwendungen**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analysieren von Ansichten und Berichten für Samplingdaten
- [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
