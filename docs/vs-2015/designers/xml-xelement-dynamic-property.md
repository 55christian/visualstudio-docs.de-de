---
title: Xml (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148046"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ruft den unformatierten XML-Inhalt des Elements ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 <xref:System.String>, die den unformatierten XML-Inhalt des Elements darstellt.  
  
## <a name="remarks"></a>Anmerkungen  
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29>-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>-Klasse, wobei der `SaveOptions`-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Wert](../designers/value-xelement-dynamic-property.md)
