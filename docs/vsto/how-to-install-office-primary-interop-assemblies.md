---
title: 'Vorgehensweise: Installieren von primären Interopassemblys für Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4b6f701e3962a25e7239c829d409a3ad69a1833a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419597"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Vorgehensweise: Installieren von primären Interopassemblys für Office
  Installieren Sie die primären Interop-Assemblys (PIAs) für Microsoft Office bei der Installation von Office.

## <a name="to-install-the-pias-when-you-install-office"></a>Zum Installieren der PIAs bei der Installation von Office

1. Stellen Sie sicher, dass Sie über eine Version von .NET Framework verfügen, die nicht älter als Version 2.0 ist.

2. Installieren Sie Microsoft Office, und stellen Sie sicher, dass die **.NET-Programmierunterstützung für** Feature aktiviert ist, für die Anwendungen, die Sie erweitern möchten (diese Funktion ist in der Standardinstallation enthalten).

    > [!WARNING]
    > Standardmäßig werden PIAS in Ihre Projektmappe eingebettet, wenn Sie sie erstellen, sodass Sie keine PIAs als Voraussetzung für die Verwendung von Ihrem VSTO-Add-in oder eine Anpassung an Benutzer verteilen.

## <a name="see-also"></a>Siehe auch
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Vorgehensweise: Verweisen Sie auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
