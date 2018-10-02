---
title: Die Struktur der Content_types] .xml-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89c5e1bab9f8cbe8cd6e2b980013c6bfdf4bc039
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524282"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Die Struktur der Content_types] .xml-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Struktur der [Content_types] .xml-Datei](https://docs.microsoft.com/visualstudio/extensibility/the-structure-of-the-content-types-dot-xml-file).  
  
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die [Content_Types] .xml-Datei zum Installieren des Pakets, aber die Datei selbst werden nicht installiert.  
  
> [!NOTE]
>  Obwohl in diesem Thema nur für XML-Dateien [Content_Type], die in VSIX-Paketen verwendet werden gilt, wird der [Content_Types] .xml-Dateityp ist Teil der *Open Packaging Conventions (OPC)* standard. Weitere Informationen finden Sie unter [OPC: A New Standard für die Paketerstellung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten wird beschrieben, das Stammelement und seine Attribute und untergeordneten Elementen.  
  
### <a name="root-element"></a>Stammelement  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich.) Der Speicherort des Schemas, die für diese [Content_Types] .xml-Datei verwendet.|  
  
### <a name="attribute-name-attribute"></a>{Attributname} Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|Der Speicherort des Schemas, Inhaltstypen.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Die `Types` Element darf eine beliebige Anzahl von `Default` Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp in das Paket muss einen eigenen verfügen `Default` Element.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Dateinamenerweiterung einer Datei in VSIX-Paket.|  
|`ContentType`|Beschreibt die Art von Inhalten, die mit der Dateinamenerweiterung verknüpft ist.|  
  
### <a name="attribute-name-attribute"></a>{Attributname} Attribut  
 Visual Studio erkennt die folgenden `ContentType` Werte für das zugeordnete `Extension` Typen.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|TXT|Text/plain|  
|PKGDEF|Text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm- oder HTML-|Text/html|  
|RTF|Anwendung/rtf|  
|PDF-Datei|Application/PDF-Datei|  
|GIF|Image/gif|  
|JPG oder JPEG-Format|Image/jpg|  
|TIFF|Image/tiff|  
|VSIX|Application/zip|  
|ZIP|Application/zip|  
|dll|application/octet-stream|  
|Alle anderen Dateitypen|application/octet-stream|  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Die folgende [Content_Types] .xml-Datei beschreibt ein typisches VSIX-Paket.  
  
### <a name="code"></a>Code  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Ein neuer Standard für das Verpacken Ihrer Daten](http://go.microsoft.com/fwlink/?LinkID=148207)
