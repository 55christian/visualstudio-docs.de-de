---
title: Ressourcen in VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696092"
---
# <a name="resources-in-vspackages"></a>Ressourcen in VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können lokalisierte Ressourcen in systemeigenen-Satelliten-UI-DLLs, verwalteter Satelliten-DLLs, oder in ein verwaltetes VSPackage selbst einbetten.  
  
 Einige Ressourcen können nicht in VSPackages eingebettet werden. Die folgenden verwalteten Typen können eingebettet werden:  
  
- Zeichenfolgen  
  
- Paketladeschlüssel (die auch Zeichenfolgen)  
  
- Toolfenstersymbole  
  
- Kompilierte Befehl Tabelle Ausgabe (CTO)-Dateien  
  
- CTO bitmaps  
  
- Befehlszeilenhilfe  
  
- Informationen zu Dialogfelddaten  
  
  Ressourcen-ID werden Ressourcen in einem verwalteten Paket ausgewählt. Eine Ausnahme ist die CTO-Datei, die CTMENU genannt werden muss. Die CTO-Datei muss angezeigt werden, in der Ressourcentabelle als eine `byte[]`. Alle anderen Ressourcenelemente werden nach Typ identifiziert.  
  
  Können Sie die <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Attribut, um anzugeben, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , dass die verwaltete Ressourcen verfügbar sind.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  Festlegen von <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> auf diese Weise gibt an, dass [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nicht verwaltete Satelliten-DLLs sollten ignoriert werden, bei der Ressourcen, z. B. mithilfe von Suche nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zwei oder mehr Ressourcen, die die Ressourcen-ID, erkennt er verwendet die erste Ressource, die es findet.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird eine verwaltete Darstellung eines Fenstersymbols Tool.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Das folgende Beispiel veranschaulicht die CTO-Byte-Array, einbetten, das wodurch die CTMENU genannt werden muss.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Verzögerungen beim Laden von VSPackages, wann immer möglich. Eine Folge Einbetten einer CTO-Datei in einem VSPackage ist, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alle solchen VSPackages im Arbeitsspeicher muss geladen werden, während des Setups der ist, wenn es sich um eine zusammengeführte Befehlstabelle erstellt. Ressourcen können aus einem VSPackage extrahiert werden, anhand der Metadaten ohne Ausführen von Code in das VSPackage. Das VSPackage ist zu diesem Zeitpunkt nicht initialisiert werden, damit der Leistungsverlust minimal ist.  
  
 Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Anforderungen eine Ressource aus einem VSPackage, nach der Installation, das Paket ist wahrscheinlich bereits geladen und initialisiert, damit der Leistungsverlust minimal ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Verwaltete VSPackages](../../misc/managed-vspackages.md)
