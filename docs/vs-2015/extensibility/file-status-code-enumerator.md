---
title: Dateistatuscode-Enumerator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204376"
---
# <a name="file-status-code-enumerator"></a>Dateistatuscode-Enumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `SccStatus` Enumerator enthält benannte Konstante Werte, die den Status einer Datei in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird verwendet, durch die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) und `POPLISTFUNC` Callback-Funktion (finden Sie unter [POPLISTFUNC](../extensibility/poplistfunc.md) Einzelheiten).  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Member  
 SCC_STATUS_INVALID  
 Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC_STATUS_NOTCONTROLLED  
 Datei ist nicht unter quellcodeverwaltung.  
  
 SCC_STATUS_CONTROLLED  
 Datei befindet sich unter quellcodeverwaltung.  
  
 SCC_STATUS_CHECKEDOUT  
 Die von den aktuellen Benutzer auf dem lokalen Datenträger ausgecheckt.  
  
 SCC_STATUS_OUTOTHER  
 Datei wird von einem anderen Benutzer ausgecheckt.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Datei wird exklusiv ausgecheckt.  
  
 SCC_STATUS_OUTMULTIPLE  
 Datei wird von mehreren Benutzern ausgecheckt.  
  
 SCC_STATUS_OUTOFDATE  
 Die Datei ist nicht das neueste.  
  
 SCC_STATUS_DELETED  
 Datei wurde aus dem Projekt gelöscht.  
  
 SCC_STATUS_LOCKED  
 Datei gesperrt ist; Es wurden keine weiteren Versionen zulässig.  
  
 SCC_STATUS_MERGED  
 Datei wurde zusammengeführt, aber noch nicht behoben bzw. überprüft.  
  
 SCC_STATUS_SHARED  
 Datei wird von Projekten gemeinsam verwendet.  
  
 SCC_STATUS_PINNED  
 Datei ist eine explizite Version freigegeben.  
  
 SCC_STATUS_MODIFIED  
 Datei wurde geändert/unterteilt/verletzt.  
  
 SCC_STATUS_OUTBYUSER  
 Datei wird vom aktuellen Benutzer ausgecheckt.  
  
 SCC_STATUS_NOMERGE  
 Datei kann nicht mit zusammengeführt werden und muss nicht gespeichert werden, bevor Sie einen GET.  
  
 SCC_STATUS_RESERVED_1  
 Für die interne Verwendung vorgesehen.  
  
 SCC_STATUS_RESERVED_2  
 Für die interne Verwendung vorgesehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
