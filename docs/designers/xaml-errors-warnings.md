---
title: XAML-Fehler und -Warnungen
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3ae795b464d8a693371b1ebb9238a897debbf02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892619"
---
# <a name="xaml-errors-and-warnings"></a>XAML-Fehler und -Warnungen

Bei der Erstellung von XAML analysiert Visual Studio den Code während Sie tippen. Wenn ein Fehler erkannt wird, erscheint eine Wellenlinie in der Codezeile. Wenn Sie mit der Maus auf die Wellenlinie zeigen, erhalten Sie Informationen zu dem Fehler bzw. der Warnung. Für einige Fehler und Warnungen wird eine Glühbirne für „Schnelle Aktion“ angezeigt. Mit der Tastenkombination **STRG**+**.** werden die Optionen zum Beheben des Problems angezeigt.

## <a name="error-types"></a>Fehlertypen

Im Hintergrund analysieren mehrere Tools gleichzeitig die XAML. XAML-Fehler werden in einen der folgenden drei Typen unterteilt, je nach Tool, mit dem der Fehler erkannt wurde:

|**Fehler erkannt von**|**Fehlercodeformat**|
| - |-----------------|
|XAML-Sprachdienst (XAML-Editor)|XLSxxxx|
|XAML-Designer|XDGxxxx|
|Bearbeiten und Fortfahren – XAML|XECxxxx|

> [!Note]
> Nicht alle Fehler oder Warnungen verfügen über einen entsprechenden Code. Solche Fehler sind in der Regel Fehler des XAML-Designers.

## <a name="suppress-xaml-designer-errors"></a>Unterdrücken von XAML-Designer-Fehlern

Öffnen Sie das Dialogfeld **Optionen**, indem Sie **Extras > Optionen** und dann **Text-Editor > XAML > Sonstiges** auswählen.

Deaktivieren Sie das Kontrollkästchen **Show errors detected by the XAML designer** (Fehler anzeigen, die vom XAML-Designer erkannt wurden).

![Unterdrücken von XAML-Designer-Fehlern](../designers/media/suppress_xaml_designer_errors.png)
