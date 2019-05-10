---
title: Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f9a4a873f2b6b3f41bd86d046bc187c17f063f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908736"
---
# <a name="services-provided-source-control-vspackage"></a>Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage)
Dienste sind der primäre Mechanismus, über dem Funktionalität von VSPackages sowie zwischen der integrierten Entwicklungsumgebung (IDE) von Visual Studio und der installierten VSPackages gemeinsam genutzt wird. Detaillierte Beschreibung der Dienste und ihre Bedeutung in der Visual Studio-IDE, finden Sie unter[verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Die Quellcodeverwaltungsdienst
 Visual Studio bietet zwei Ebenen von Diensten, die Dienste auf IDE-Ebene und auf Paketebene Dienste. Visual Studio-IDE bietet nativ Dienste auf IDE-Ebene. Das Quellcodeverwaltungspaket nutzt einige dieser Dienste. Der Quellcode-Verwaltungspaket als ein VSPackage teilt die Quellcodeverwaltungsfunktionen durch einen eigenen privaten quellcodeverwaltungsdienst bereitstellen. Das Quellcodeverwaltungspaket kapselt den Satz von Steuerelementen-Schnittstellen implementiert werden in Form eines Vertrags, der von Visual Studio-IDE verwendet werden kann.

## <a name="see-also"></a>Siehe auch
- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)