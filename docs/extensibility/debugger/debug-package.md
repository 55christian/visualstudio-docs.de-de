---
title: Debuggen-Pakets | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb1af813fabb1245d85fe18629d77a45f6acca3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345905"
---
# <a name="debug-package"></a>Debug-Paket
Das debugpaket in der Visual Studio-Shell ausgeführt und verarbeitet alle der Benutzeroberfläche. Es nutzt die Visual Studio Debuggen von Schnittstellen und kommuniziert mit der Sitzungs-Manager (SDM).

 Unterbrechungsbezogene Ereignisse, die durch die SDM gesendete wechseln Ausführungsmodus den Debugger Unterbrechungsmodus ein, und ändern Sie die Anwendung, in dem die Unterbrechung aufgetreten ist. Das debugpaket verfolgt den Stapelrahmen und den Thread aus den Informationen, die an ihn gesendet wird, durch die Ereignisse an.

 Das debugpaket, weist keine Sprache oder Laufzeitumgebung Abhängigkeiten. Es ist nicht erforderlich, das debugpaket zu implementieren.

 Das debugpaket wird implementiert, indem *vsdebug.dll*.

## <a name="see-also"></a>Siehe auch
- [Sitzungsbasierter Debug-manager](../../extensibility/debugger/session-debug-manager.md)
- [Stapelrahmen](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)