---
title: 'DA0506: Maximale private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd3ae6b45d910723f04cf8b828cbce62f8fdc1a7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935905"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Höchstwert für „Private Bytes“, der dem Prozess, für den die Profilerstellung ausgeführt wird, zugeordnet ist

|||
|-|-|
|Regel-ID|DA0506|
|Kategorie|Ressourcenüberwachung|
|Profilerstellungsmethode|Alle|
|Meldung|Diese Information wurde lediglich zu Informationszwecken erhoben. Vom Leistungsindikator für die Verarbeitung privater Bytes wird der virtuelle Speicher ermittelt, der von dem Prozess belegt wird, für den die Profilerstellung ausgeführt wird. Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|
|Regeltyp|Information|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="rule-description"></a>Regelbeschreibung
 In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher in (privaten) Bytes angegeben, die derzeit vom Prozess belegt sind. Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.

 Für 32-Bit-Prozesse, die auf einem 32-Bit-Computer ausgeführt werden, beträgt die Obergrenze des privaten Teils des Prozessadressbereichs 2 GB. Bei Verwendung des Boot.ini-Schalters [/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) können für 32-Bit-Prozesse bis zu 3 GB an virtuellem Arbeitsspeicher zur Verfügung gestellt werden. Für einen 32-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 4 GB an privatem virtuellem Arbeitsspeicher zur Verfügung.

 Für einen 64-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 8 TB an privatem virtuellem Arbeitsspeicher zur Verfügung.

 Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.

 Weitere Informationen zu Prozessadressräumen finden Sie unter [Virtual Address Space (Virtueller Adressraum)](http://go.microsoft.com/fwlink/?LinkId=177832) in der Dokumentation zur Speicherverwaltung unter Windows.

## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten
 Mithilfe des gemeldeten Werts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarios nachvollziehen.

 Nähert sich der maximale Wert der privaten Bytes eines Prozesses der architekturbedingten Maximalgröße eines Prozessadressbereichs, können durch ungenügenden Arbeitsspeicher bedingte Ausnahmen auftreten. Weitere Informationen finden Sie unter [Investigating Memory Issues (Untersuchen von Arbeitsspeicherproblemen)](http://go.microsoft.com/fwlink/?LinkID=177833) in den MSDN Magazine-Ausgaben.