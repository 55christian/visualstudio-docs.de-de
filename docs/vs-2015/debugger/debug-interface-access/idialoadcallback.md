---
title: IDiaLoadCallback | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b26a638c1ac8bd808bae6fa78aaa3cc24dedede5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151958"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Empfängt Rückrufe aus dem DIA-Symbol, suchen die Prozedur, sodass eine Benutzeroberfläche, über den Fortschritt des Versuchs Standort Berichten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle verfügbar gemacht:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Aufgerufen, wenn ein Debugverzeichnis in die .exe-Datei gefunden wurde.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wird aufgerufen, wenn eine Kandidat DBG-Datei geöffnet wurde.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Aufgerufen, wenn eine Kandidat PDB-Datei geöffnet wurde.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Bestimmt, ob die Registrierung Abfragen verwendet werden können, um Symbolsuchpfade zu suchen.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Bestimmt, ob der Zugriff auf einen anderen Symbolserver zugelassen wird, um Symbole aufzulösen.|  
  
## <a name="remarks"></a>Hinweise  
 Die Client-Anwendung implementiert diese Schnittstelle und stellt einen Verweis auf die er im Aufruf der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
 Zusätzliche Einschränkungen, die für einen Load-Prozess festgelegt werden können, finden Sie unter den [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
