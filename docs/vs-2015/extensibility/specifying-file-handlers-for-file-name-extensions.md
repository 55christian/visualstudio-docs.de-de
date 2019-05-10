---
title: Angeben von Dateihandlern für Dateierweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fe2f26a959fc6a185bf244bfa4571846b7991a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447190"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Angeben von Dateihandlern für Dateierweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt eine Reihe von Möglichkeiten, um die Anwendung zu ermitteln, die eine Datei behandelt, die eine bestimmte Dateierweiterung hat. Die Verben OpenWithList und OpenWithProgids werden zwei Möglichkeiten zum Angeben von dateihandlern unter dem Registrierungseintrag für die Dateierweiterung.  
  
## <a name="openwithlist-verb"></a>OpenWithList Verb  
 Wenn Sie eine Datei im Windows-Explorer mit der rechten Maustaste, sehen Sie die **öffnen** Befehl. Wenn mehr als ein Produkt mit der Erweiterung zugeordnet ist, sehen Sie ein **Öffnen mit** Untermenü.  
  
 Sie können verschiedene Anwendungen, öffnen Sie eine Erweiterung durch Festlegen des OpenWithList-Schlüssels für die Dateierweiterung in HKEY_CLASSES_ROOT registrieren. Die Anwendungen, die unter diesem Schlüssel für eine Dateierweiterung aufgeführt werden, unter der **Empfohlene Programme** Überschrift in der **Öffnen mit** Dialogfeld. Das folgende Beispiel zeigt die Anwendungen, die zum Öffnen der VCPROJ-Dateierweiterung registriert.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
> Angeben von Anwendungen bei Schlüsseln wird aus der Liste unter HKEY_CLASSES_ROOT\Applications.  
  
 Hinzufügen eines Schlüssels OpenWithList, deklarieren Sie, dass Ihre Anwendung eine Dateierweiterung unterstützt, auch wenn eine andere Anwendung Eigentümer der Erweiterung wird. Dies kann einer zukünftigen Version Ihrer Anwendung oder eine andere Anwendung sein.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Den programmatischen Bezeichner (ProgIDs) gibt die Anzeigenamen Versionen ClassIDs, die eine Version einer Anwendung oder COM-Objekt zu identifizieren. Alle gemeinsam erstellbares Objekt muss es sich um eine eigene ProgID sein. VisualStudio.DTE.7.1 startet z. B. Visual Studio .NET 2003, während VisualStudio.DTE.10.0 startet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Als Besitzer eines Projekttyps oder Projektelementtyp müssen Sie eine bestimmte Version ProgID für die Dateierweiterung erstellen. Diese ProgIDs möglicherweise redundant sein, da mehr als eine ProgID die gleiche Anwendung starten kann. Weitere Informationen finden Sie unter [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Verwenden Sie die folgende Benennungskonvention für eine Datei mit versionsabhängige Programm-IDs, um bei der Registrierung von anderen Anbietern tragen:  
  
|Dateierweiterung|Mit versionsverwaltung durch das Programm-ID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Sie können verschiedene Anwendungen, die auf eine bestimmte Dateierweiterung zu öffnen, indem Sie mit versionsverwaltung durch das Programm-IDs als Werte hinzufügen, in der HKEY_CLASSES_ROOT können registrieren\\*\<Erweiterung >* \OpenWithProgids Schlüssel. Dieser Registrierungsschlüssel enthält eine Liste von alternativen Programm-IDs, die mit der Dateinamenerweiterung verknüpft ist. Die Anwendungen, die die aufgelisteten versionsabhängige Programm-IDs zugeordnet werden im der **Öffnen mit**_Produktname_ Untermenü. Wenn dieselbe Anwendung, sowohl angegeben wird die `OpenWithList` und `OpenWithProgids` Schlüssel, das Betriebssystem führt die Duplikate.  
  
> [!NOTE]
> Die `OpenWithProgids` Schlüssel wird nur in Windows XP unterstützt. Da andere Betriebssysteme diesem Schlüssel ignorieren möchten, nicht verwenden Sie sie als die einzige Registrierung für Dateihandler. Verwenden Sie diesen Schlüssel, um eine bessere benutzererfahrung in Windows XP bereitzustellen.  
  
 Fügen Sie das gewünschte Programm-IDs als Werte des Typs REG_NONE hinzu. Der folgende Code bietet ein Beispiel für das Registrieren von Programm-IDs für eine Dateierweiterung (. *Ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Die ProgID angegeben, wie der Standardwert für die Dateierweiterung der Standardhandler für die Datei ist. Wenn Sie die ProgID für eine Erweiterung ändern, die mit einer früheren Version von geliefert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder, die von anderen Anwendungen erstellt werden können, und Sie müssen sich registrieren der `OpenWithProgids` Schlüssel für die Dateierweiterung aus, und geben Sie die neue ProgID in der Liste zusammen mit der alte versionsabhängige Programm-IDs, die Sie unterstützen. Zum Beispiel:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Wenn die alte ProgID Verben zugeordnet, diese Verben werden auch angezeigt, unter **Öffnen mit** *Produktname* im Kontextmenü die Option.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zu Dateierweiterungen](../extensibility/about-file-name-extensions.md)   
 [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
