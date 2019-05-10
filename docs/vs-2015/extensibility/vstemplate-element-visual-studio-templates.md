---
title: VSTemplate-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8219f12eed091858a43c2bd5092b8b06f8320bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422905"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält alle Metadaten für die Projektvorlage, Item-Vorlage oder Starterkits.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Type`|Gibt die Vorlage als eine Projektvorlage oder eine Elementvorlage. Dieses Attribut kann den Wert der haben `Project` oder `Item`.|  
|`Version`|Gibt eine Versionsnummer für die Vorlage an. Vorlagen in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] und [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] haben eine `Version` -Attributwert `3.0.0`.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt an, Daten, die kategorisiert die Vorlage und definiert, wie es in angezeigt. die **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Inhalt der Vorlage.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Optionales Element.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Optionales Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Die `VSTemplate` Element ist das Stammelement der VSTEMPLATE-Dateien.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Anwendung veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
