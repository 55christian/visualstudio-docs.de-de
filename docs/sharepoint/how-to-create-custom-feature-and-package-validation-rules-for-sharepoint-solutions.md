---
title: 'SharePoint-Lösungen: Benutzerdefinierte Funktion erstellen, Packen von Validierungsregeln'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a10118a0c83f9e17e32efd293a9a824e38a0942a
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835935"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Vorgehensweise: Erstellen Sie, benutzerdefinierte Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen
  Sie können benutzerdefinierte Validierungsregeln, um zu überprüfen, ob das Projektmappenpaket generiert, die von Visual Studio erstellen. Sie können vollständige Überprüfung auf ein ganzes Feature oder Paket ausführen, dazu **überprüfen** aus dem Kontextmenü eines Pakets oder einer Funktion in der **PackagingExplorer**. Teilweise Validierung wird ausgeführt, wenn Sie die neue SharePoint-Projektelemente oder Funktionen, auf das Projekt hinzufügen, um zu bestimmen, ob das Paket oder eine Funktion in einem gültigen Zustand wäre.

### <a name="to-create-a-custom-package-validation-rule"></a>Um eine benutzerdefinierte Paketvalidierungsregel zu erstellen.

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die eine der folgenden Schnittstellen implementiert:

    - Um eine Paketvalidierungsregel zu erstellen, implementieren die <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> Schnittstelle.

    - Um eine Validierungsregel für die Funktion zu erstellen, implementieren die <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Schnittstelle.

4. Hinzufügen der <xref:System.ComponentModel.Composition.ExportAttribute> der-Klasse. Mit diesem Attribut können Visual Studio zum Ermitteln und laden die Validierungsregel. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> oder <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Typ an den Attributkonstruktor.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie eine benutzerdefinierte Funktionsvalidierungsregel zu erstellen.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint.

- System.ComponentModel.Composition.

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für die SharePoint-tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
