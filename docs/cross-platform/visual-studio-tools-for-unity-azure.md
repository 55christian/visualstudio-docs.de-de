---
title: Programmieren mit Visual Studio-Tools für Unity und Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/18/2017
ms.reviewer: crdun
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: e9a07a7f04cae433803d012302555821fc851075
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916825"
---
# <a name="program-with-unity-and-azure"></a>Programmieren mit Unity und Azure

Azure bietet eine skalierbare Lösung zum Speichern von Telemetriedaten und anderen Spieledaten in der Cloud. Mit der Veröffentlichung von Unity 2017 wird die Azure-Integration durch die experimentelle Unterstützung von Unity für .NET 4.6 so einfach wie nie, da die Verwendung von Azure .NET SDKs zugelassen wird.

## <a name="experimental-azure-sdks"></a>Experimentelle Azure SDKs

> [!NOTE]
> Diese SDKs werden zwar nicht unterstützt, jedoch bereitgestellt, um Kunden das Testen der experimentellen .NET 4.6-Unterstützung von Unity zu ermöglichen.

Besuchen Sie die [Sandbox](/sandbox/), um die folgenden experimentellen Azure SDKs mit Unity zu testen:

* [Azure Storage SDK für Unity](/sandbox/gamedev/unity/azure-storage-unity?wt.mc_id=azgamedev-sandbox-brpeek)
* [Azure Event Hubs SDK für Unity](/sandbox/gamedev/unity/azure-event-hubs-unity?WT.mc_id=azgamedev-sandbox-brpeek)
* [Azure Mobile Apps SDK für Unity](/sandbox/gamedev/unity/azure-mobile-apps-unity?WT.mc_id=azgamedev-sandbox-brpeek)

## <a name="azure-sdk-sample"></a>Azure SDK-Beispiel

Es gibt auch ein [einfaches Beispielspiel](/sandbox/gamedev/unity/samples/azure-mobile-apps-unity-racer), bei dem das Azure SDK für einfache Tabellen und Unity zum Einsatz kommen. Das Spiel verwendet den Azure-Datenspeicher für einfache Tabellen, um die Bestenliste mit den höchsten Punktzahlen im Auge zu behalten und In-Game-Telemetriedaten zu speichern. Es steht [über GitHub zum Download zur Verfügung](https://github.com/BrianPeek/AzureSamples-Unity).

![Screenshot eines Spielbeispiels](media/vstu_azure-test-sample-game-image2.png)
