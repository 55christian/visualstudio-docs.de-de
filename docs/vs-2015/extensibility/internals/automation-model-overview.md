---
title: Übersicht über das Automatisierungsmodell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699511"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungsmodell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Automatisierungsmodell besteht aus einem Satz von Objekten, die mit denen Sie ein Visual Studio-add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die Visual Studio-Umgebung bearbeiten kann, und Automatisieren allgemeiner Aufgaben. Visual Studio-Erweiterung kann Erstellen von benutzerdefinierten Komponenten für Visual Studio oder die Funktionalität des standard-Komponenten wie z. B. den Text-Editor hinzufügen.  
  
## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungsmodell  
 Das Automatisierungsmodell bestehen aus miteinander verbundene Gruppen von Objekten, die wesentliche Merkmale der gemeinsamen Umgebung zu steuern. Im folgenden finden ein Diagramm mit den umfassenden Satz von Objekten, die das Automatisierungsmodell zu erstellen.  
  
 ![Diagramm des Visual Studio-Automatisierung](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "VsVisualStudioAutomationObjectChart")  
Visual Studio-Automatisierungsobjekte  
  
 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Die Umgebung bietet ein Modell für verschiedene Funktionsbereiche. Es ist z. B. ein Codemodell für verschiedene Elemente, die Sie ggf. im Code finden. Es gibt ein Dokumentmodell für die verschiedenen Elemente des Dokuments. Ein Bereich, der Projektbereich ist von besonderem Interesse für VSPackage-Anbieter. Möchten Sie wahrscheinlich Ihre neue Projekttypen mitwirken am Automatisierungsmodell in die gleiche Weise wie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] zum Automatisierungsmodell beitragen. Dass der Prozess in beschriebene [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Stellen, in dem Sie die Erweitern des Automatisierungsmodells der Umgebung berücksichtigen können:  
  
- Projekt  
  
- Dokument  
  
- Code  
  
- Build  
  
  Weitere Informationen zu Automation finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). In diesem Dokument und die Dokumente wird Links, um Ihnen zu treffen von Entscheidungen in Bezug auf, wie Sie Automation für das VSPackage bereitgestellt werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen einer Add-Ins](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
