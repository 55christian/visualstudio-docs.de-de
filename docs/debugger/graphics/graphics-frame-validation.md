---
title: Graphics Frame-Überprüfung | Microsoft-Dokumentation
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce283e5cbab30b612a02ec447113ad11e206a7f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895869"
---
# <a name="graphics-frame-validation"></a>Grafik-Frame-Überprüfung
<!-- VERSIONLESS -->
Visual Studio 2017 und höher unterstützt die **Frame-Überprüfung** Tool.  Die Frame-Überprüfung-Fenster werden Fehler und Warnungen im Zusammenhang mit der Ereignisliste angezeigt.  Um dieses Fenster anzuzeigen, wählen die **Ansicht > Frame-Überprüfung** Menü.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie auf die **Überprüfung ausführen** auf der linken oberen Ecke, um die Analyse zu initiieren.  Es dauert mehrere Minuten je nach Komplexität des Frames.  Die Daten, die angezeigt wird, hier ist eine Kombination aus beiden Quellen: die Nachrichten, D3D selbst ausgibt, wenn [SDK Layers](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) aktiviert ist, und die Daten, die vom Nachverfolgen von internen Zustand des Tools gesammelt werden. Nach Abschluss des Vorgangs sehen Sie mehrere Spalten mit Daten:

| **Spalte** | **Beschreibung** |
|------------| - |
| Ereignis-ID | ID, die zugeordnet ein Eintrag in wird der [Ereignisliste](graphics-event-list.md) Fenster. |
| Schweregrad | Beschädigung, Fehler, Warnung, Informationen oder Nachricht. |
| Kategorie | Anwendung definiert ist, verschiedene, Initialisierung, Bereinigung, Kompilierung, Status erstellen, Status festlegen, Status abrufen, Ausführung, Bearbeitung von Ressourcen und redundante und nicht verwendete-Shader. |
| Meldung | Die Meldung, die dem Ereignis zugeordnet wird. |
| event | Das Ereignis, das den Fehler oder die Warnung zugeordnet. |

## <a name="see-also"></a>Siehe auch
[Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->