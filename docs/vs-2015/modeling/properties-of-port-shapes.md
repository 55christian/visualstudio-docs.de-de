---
title: Eigenschaften von Anschlussformen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 206f13610b22253a3b711413721411a1ff075570
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959518"
---
# <a name="properties-of-port-shapes"></a>Eigenschaften von Anschlussformen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Anschluss-Formen verwenden, um Domänenklassen im generierten Designer darzustellen.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Anschluss-Formen haben Eigenschaften, die in der folgenden Tabelle aufgeführt sind.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|  
|Der Farbverlaufmodus|Die füllverlaufsmodus dieser Form.|Horizontal|  
|Geometry|Die Geometrie dieser Form (Rechteck, abgerundetes Rechteck, Ellipse oder Kreis).|Rechteck|  
|Verfügt über Standard-Verbindungspunkte|Wenn `True`, verwendet die Form oben, unten, links und rechten Verbindungspunkte im generierten Designer.|False|  
|Konturfarbe|Die Konturfarbe dieser Form.|Schwarz|  
|Konturstrichstil|Der konturstrichstil dieser Form (einfarbig, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|  
|Umrissstärke|Die konturlinienstärke dieser Form.|0.03125|  
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die mit dieser Form verknüpft sind.|Schwarz|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von dieser Form generiert wird.|\<none>|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, die vom Port generiert wird (`none`, `abstract` oder `sealed`).|none|  
|Basisport|Die Basisklasse dieser Form.|(keine)|  
|Name|Der Name dieser Form.|Aktuelle name|  
|Namespace|Der Namespace, der diese Form zugeordnet ist.|Aktuellen namespace|  
|Tipp Tooltyp|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn fest, klicken Sie dann den Wert des der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet, wenn die Variable, klicken Sie dann die QuickInfo wird im benutzerdefinierten Code definiert.|none|  
|Hinweise|Informelle Hinweise, die mit dieser Form verknüpft sind.|\<none>|  
|Die ursprüngliche Höhe|Die ursprüngliche Höhe dieser Form in Zoll.|1|  
|Die ursprüngliche Breite|Die ursprüngliche Breite dieser Form in Zoll.|1.5|  
|Als Eigenschaft verfügbar gemachte Füllfarbe<br /><br /> Verfügbar gemachte Füllverlaufsmodus<br /><br /> Konturfarbe als Eigenschaft verfügbar gemacht.<br /><br /> Konturstrichstil als Eigenschaft verfügbar gemacht.<br /><br /> Umrissstärke als Eigenschaft verfügbar<br /><br /> Stellt Text Color|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste in der Definition der Form, und klicken Sie auf **verfügbare hinzufügen**.|False|  
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<none>|  
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt werden soll.|\<none>|  
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<none>|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Form verwendet wird.|\<none>|  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
