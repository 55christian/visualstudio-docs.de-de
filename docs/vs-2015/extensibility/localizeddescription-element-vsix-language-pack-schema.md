---
title: LocalizedDescription-Element (Schema für VSIX-Sprachpaket) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 281f3823d22ee0e290e4b6bb32a8280f4773a592
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679909"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription-Element (Schema für VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Stellt eine lokalisierte Beschreibung der Erweiterung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Keiner||  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keiner||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSIX-LanguagePack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Erforderlich. Stellt das Stammelement für ein VSIX-Sprachpaket bereit.|  
  
## <a name="text-value"></a>Textwert  
 Erforderlich. Eine textbeschreibung der Erweiterung in der Zielsprache.  
  
## <a name="element-information"></a>Elementinformationen  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Schemaname   |                 Schema für das VSIX-Sprachpaket                 |
| Validierungsdatei |                VSIXLanguagePackSchema.xsd                 |
|  Leer kann sein   |                      Nicht zutreffend                       |
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz für VSX Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
