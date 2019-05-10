---
title: KeyBinding-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958538"
---
# <a name="keybinding-element"></a>KeyBinding-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding-Element gibt die Tastenkombinationen für die Befehle an.  
  
 Befehle können sowohl bei Einzel- oder dualcontrollern tastenzuordnungen zugeordnet haben. Ein Beispiel für eine einzelne tastenzuordnung ist STRG + S, für die **speichern** Befehl. Duale tastenzuordnungen erfordern zwei aufeinander folgenden Tastenkombinationen einen Befehl ausgelöst. Ein Beispiel für eine duale tastenzuordnung ist STRG + K, STRG + K, ein Lesezeichen festlegen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich.|  
|id|Erforderlich.|  
|Editor|Erforderlich. Der Editor GUID gibt an, der Bearbeitungskontext für den diese Tastenkombination aktiv sein werden. Der globale Bindung Bereichswert ist "guidVSStd97".|  
|key1|Erforderlich. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X und VK_constants vorangestellt.|  
|mod1|Dies ist optional. Eine beliebige Kombination aus STRG, ALT und die UMSCHALTTASTE, die durch Leerzeichen getrennt sind.|  
|key2|Dies ist optional. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X und VK_constants vorangestellt.|  
|mod2|Dies ist optional. Eine beliebige Kombination aus STRG, ALT und die UMSCHALTTASTE, die durch Leerzeichen getrennt sind.|  
|Emulator|Dies ist optional.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element||  
|Anmerkung||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Gruppen KeyBinding-Elementen und anderen KeyBindings Gruppierungen.|  
  
## <a name="example"></a>Beispiel  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [KeyBindings-Element](../extensibility/keybindings-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
