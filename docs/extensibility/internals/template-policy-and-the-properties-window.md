---
title: Vorlagenrichtlinie und das Fenster "Eigenschaften" | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 751e6d766a4ae107eaabb7364d8aeca627fc59da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331212"
---
# <a name="template-policy-and-the-properties-window"></a>Vorlagenrichtlinie und das Eigenschaftenfenster
Wenn ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, kann diese Enterprise-Vorlagenprojekt Richtlinie erzwingen. Richtlinie wird ein einschränkende System, das verwendet werden kann, legen Sie Standardwerte für Eigenschaften, Eigenschaften ausblenden, Hinzufügen von Eigenschaften und so weiter.

 Mit der Richtlinie zum Steuern der Anzeige von Informationen in den **Eigenschaften** Fenster unterscheidet sich von der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Eigenschaften des Objekts auf der Komponentenebene, verarbeitet, während der Richtlinie verwendet werden kann, um Objekteigenschaften Ebene der Projektmappe oder das Projekt zu beschränken. Mit anderen Worten,

- Implementieren Sie die Methoden auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> um zu bestimmen, was in angezeigt wird der **Eigenschaften** Fenster für bestimmte Objekte

- Richtlinie der Ebene der Projektmappen- und Projektdateien verwenden, um zu bestimmen, was in angezeigt wird der **Eigenschaften** Fenster für die zuvor angegebenen Objekte

  Verwendung der Richtlinie um selektiv bestimmte Eigenschaften im beschränken die **Eigenschaften** anzeigen, wenn ein Projektelement eines angegebenen Typs ausgewählt ist **Projektmappen-Explorer** kann vorteilhaft sein, alle Mitglieder der das Entwicklungsteam an einem Projekt arbeiten. Z. B. können mit der Richtlinie an, Sie alle Verbindungszeichenfolgen-Informationen in einer Datenbank für Ihre Entwickler einrichten und Aktivieren des Schreibschutzes für der Verbindungszeichenfolge. Auf diese Weise können Sie angeben, dass eine einfache Möglichkeit, sicherzustellen, dass jeder Entwickler über den richtigen Pfad für den Datenzugriff verwendet.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)