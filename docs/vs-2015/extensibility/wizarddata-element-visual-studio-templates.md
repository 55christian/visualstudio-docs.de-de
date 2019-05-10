---
title: WizardData-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d7cd59266a69140ba2ea5a7fd1d1b0b0c72f14c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960388"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt an, benutzerdefinierte XML-Datei  
  
 \<VSTemplate>  
 \<WizardData>  
  
## <a name="syntax"></a>Syntax  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, Item-Vorlage oder Starterkits.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist optional.  
  
 Dieser Text gibt den benutzerdefinierten XML-Code für die Übergabe an die im angegebenen benutzerdefinierten Assistenten-Erweiterung der [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) Element.  
  
## <a name="remarks"></a>Hinweise  
 Beliebige XML-Daten kann in diesem Element angegeben werden. Der XML-Code wird als Parameter an die Erweiterung für benutzerdefinierte Assistentenseiten, übergeben werden können die Dateierweiterung an den Inhalt dieses Elements verwendet. Auf diese Daten nicht überprüft.  
  
 Den Inhalt der `WizardData` Element übergeben werden, nicht geändert, als Parameter in das Zeichenfolgenwörterbuch von Parametern in der `IWizard.RunStarted` Methode. Der Parameter den Namen $WizardData$.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für die standard-Projektvorlage für eine [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows-Anwendung.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
