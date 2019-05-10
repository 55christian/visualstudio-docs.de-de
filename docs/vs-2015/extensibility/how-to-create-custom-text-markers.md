---
title: 'Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435980"
---
# <a name="how-to-create-custom-text-markers"></a>Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen benutzerdefinierten Text-Marker, um hervorzuheben oder Organisieren Code erstellen möchten, müssen Sie die folgenden Schritte ausführen:  
  
- Registrieren Sie die neue textmarkierung, sodass andere Tools, die darauf zugreifen können  
  
- Geben Sie einen Standardimplementierung und Konfiguration der textmarkierung  
  
- Erstellen ein Diensts, der von anderen Prozessen verwendet werden kann, zu der textmarkierung verwenden  
  
  Weitere Informationen darüber, wie Sie eine textmarkierung für einen Codebereich gelten, finden Sie unter [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Um eine benutzerdefinierte Markierung zu registrieren.  
  
1. Erstellen Sie einen Registrierungseintrag wie folgt:  
  
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* \Text Editor\External Markers\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID ></em>ist eine `GUID` zum Identifizieren des Markers, der hinzugefügt wird  
  
    *\<Version >* ist die Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. 8.0  
  
    *\<PackageGUID >* ist die GUID des VSPackage das Automatisierungsobjekt implementieren.  
  
   > [!NOTE]
   > Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann mit einem alternativen Stamm überschrieben werden, wenn die Visual Studio-Shell, können Sie auch weitere Informationen finden Sie unter initialisiert wird [Befehlszeilenschalter](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Erstellen Sie vier Werte unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* \Text Editor\External Marker\\*\<MarkerGUID >*  
  
   - (Standard)  
  
   - Dienst  
  
   - DisplayName  
  
   - Package  
  
   - `Default` ist eine optionale Eingabe des Typs REG_SZ. Wenn festgelegt, ist der Wert des Eintrags, eine Zeichenfolge, enthält einige nützliche identifizierende Informationen, z. B. "benutzerdefinierte Textmarkierung" auf.  
  
   - `Service` ist ein Eintrag des Typs REG_SZ enthält die GUID-Zeichenfolge des Diensts, der die benutzerdefinierten textmarkierung von proffering bietet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Das Format ist {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` Dies ist für ein Eintrag vom Typ: REG_SZ die Ressourcen-ID mit dem Namen der benutzerdefinierten textmarkierung enthält. Das Format ist #YYYY.  
  
   - `Package` ist der Eintrag des Typs REG_SZ, enthält die `GUID` des VSPackage, das der Dienst bietet Service aufgeführt. Das Format ist {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Erstellen Sie einen benutzerdefinierten Text-marker  
  
1. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>-Schnittstelle.  
  
     Die Implementierung dieser Schnittstelle definiert das Verhalten und Aussehen Ihrer benutzerdefinierten Markertyps.  
  
     Diese Schnittstelle wird aufgerufen, wenn  
  
    1. Ein Benutzer startet die IDE zum ersten Mal an.  
  
    2. Auswahl der **Standard wiederherstellen** Schaltfläche der **Schriftarten und Farben** Eigenschaftenseite in der **Umgebung** Ordner auf den linken Bereich des der  **Optionen** erhalten Sie im Dialogfeld aus der **Tools** im Menü der IDE.  
  
2. Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> Methode, die angeben, welche `IVsPackageDefinedTextMarkerType` Implementierung sollte zurückgegeben werden basierend auf den Typ des Markers GUID, die im Aufruf Methode angegeben.  
  
     Die Umgebung ruft dieser Methode die erste Zeit Ihrer benutzerdefinierten Markertyp wird erstellt, und gibt eine GUID, die den benutzerdefinierten Markertyp identifiziert.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Auf Ihrem Typ des Markers als Dienst aussprechen.  
  
1. Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> -Methode für <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> zurückgegeben wird.  
  
2. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> -Methode, gibt die GUID, die Ihre benutzerdefinierten Marker-typdienst erkennen und bereitstellen, einen Zeiger auf die Implementierung von der <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle. Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Implementierung sollte einen Zeiger zurückgeben, für Ihre Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> Schnittstelle.  
  
     Ein eindeutiges Cookie identifiziert werden, wird Ihr Dienst zurückgegeben werden. Sie können dieses Cookie später verwenden, widerrufen Sie Ihre benutzerdefinierten Marker-typdienst durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle, die die Angabe dieses Werts Cookie.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Standard-Text-Marker hinzufügen](../extensibility/how-to-add-standard-text-markers.md)   
 [Vorgehensweise: Implementieren von Fehlermarker](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
