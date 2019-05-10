---
title: 'Vorgehensweise: Verwenden von GetGlobalService | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62948181"
---
# <a name="how-to-use-getglobalservice"></a>Vorgehensweise: Verwenden von GetGlobalService
Manchmal müssen Sie zum Abrufen eines Diensts aus einem Toolfenster oder steuern, Container, der ist nicht positioniert wurde, andernfalls ist bei einem Dienstanbieter, der nicht über den Dienst kennt gewünschten positioniert wurde. Beispielsweise empfiehlt es sich zum Schreiben in das Aktivitätsprotokoll in einem Steuerelement aus. Weitere Informationen zu diesen und andere Szenarien finden Sie unter [Vorgehensweise: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md).  
  
 Sie können die meisten abrufen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Diensten durch Aufrufen der statischen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basiert auf einer zwischengespeicherten Dienstanbieter, der zum ersten Mal initialisiert wird jedem VSPackage abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> positioniert ist. Sie müssen sicherstellen, dass diese Bedingung erfüllt ist, andernfalls ein null-Dienst vorbereitet sein.  
  
 Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ordnungsgemäß in den meisten Fällen funktioniert.  
  
- Wenn eine VSPackage ein Dienst, der nur auf einem anderen VSPackage bezeichnet bereitstellt, ist das VSPackage, die die Dienste anfordern positioniert, vor dem VSPackage, das, dass der Dienst geladen werden.  
  
- Wenn von einem VSPackage ein Toolfenster erstellt wird, ist das VSPackage positioniert, bevor das Toolfenster erstellt wird.  
  
- Wenn ein Toolfenster erstellt, die von einem VSPackage ein Steuerelementcontainer gehostet wird, ist das VSPackage positioniert, bevor der Steuerelement-Container erstellt wird.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Um einen Dienst in einem Werkzeugcontainer Fensters oder Steuerelements zu erhalten.  
  
- Fügen Sie diesen Code im Konstruktor, Toolfenster oder Control-Containers an:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Dieser Code erhält einen SVsActivityLog-Dienst, und wandelt ihn um ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)