---
title: IDiaStackWalkFrame | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150140"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stack Kontext zwischen den Aufrufen der verwaltet die [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaStackWalkFrame`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Ruft den Wert eines Registers.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Legt den Wert eines Registers.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Liest Arbeitsspeicher aus Image an.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Sucht den angegebenen Stapelrahmen für die nächste Funktion Absenderadresse an.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Sucht den angegebenen Stapelrahmen für eine Absenderadresse an oder in der Nähe der angegebenen Adresse an.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird verwendet, während der Ausführung des Programms zum Lesen und Schreiben von Register als auch auf Speicher zugreifen und Absenderadressen finden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Client-Anwendung implementiert diese Schnittstelle und übergibt eine Instanz der Schnittstelle, die [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) Methode. Die gleiche Instanz dieser Schnittstelle wird wieder verwendet, um den Status der Register bei jedem Aufruf des verwalten die `execute` Methode. Die `execute` Methode verwendet auch diese Schnittstelle, um zu bestimmen, die Rückgabeadresse.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
