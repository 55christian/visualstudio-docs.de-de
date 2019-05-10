---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 900e8db238ee26e0a7015c2acc1741a1917c8cb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564072"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:

```cpp
void YourClientDump(void *, size_t)
```

 Das bedeutet, dass die Hookfunktion einen **void**-Zeiger auf den Anfang des Zuweisungsblocks sowie einen Wert vom Typ **size_t**, der die Zuweisungsgröße angibt, akzeptieren und `void` zurückgeben muss. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.

 Nachdem Sie die Hookfunktion mithilfe von [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient) installiert haben, wird sie bei jedem Dump eines `_CLIENT_BLOCK`-Blocks aufgerufen. Mithilfe von [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) können Sie anschließend Informationen zum Typ oder Untertyp der im Dump ausgegebenen Blöcke abrufen.

 Der Zeiger auf die Funktion, den Sie an `_CrtSetDumpClient` übergeben, ist vom Typ **_CRT_DUMP_CLIENT**, wie in „CRTDBG.H“ definiert:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Siehe auch

- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)
- [crt_dbg2, Beispiel](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)