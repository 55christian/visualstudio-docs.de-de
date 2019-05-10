---
title: FRAMEINFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e5a930e81ff1105ba93ce3c3cff10ee8bff2f7e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538433"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Informationen für ein Stack-Frame-Objekt abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Member  
 FIF_FUNCNAME  
 Initialisieren und Verwenden der `m_bstrFuncName` Feld.  
  
 FIF_RETURNTYPE  
 Initialisieren und Verwenden der `m_bstrReturnType` Feld.  
  
 FIF_ARGS  
 Initialisieren und Verwenden der `m_bstrArgs` Feld.  
  
 FIF_LANGUAGE  
 Initialisieren und Verwenden der `m_bstrLanguage` Feld.  
  
 FIF_MODULE  
 Initialisieren und Verwenden der `m_bstrModule` Feld.  
  
 FIF_STACKRANGE  
 Initialisieren und Verwenden der `m_addrMin` und `m_addrMax` (Stapel-Bereich) Felder.  
  
 FIF_FRAME  
 Initialisieren und Verwenden der `m_pFrame` Feld.  
  
 FIF_DEBUGINFO  
 Initialisieren und Verwenden der `m_fHasDebugInfo` Feld.  
  
 FIF_STALECODE  
 Initialisieren und Verwenden der `m_fStaleCode` Feld.  
  
 FIF_ANNOTATEDFRAME  
 Initialisieren und Verwenden der `m_fAnnotatedFrame` Feld.  
  
 FIF_DEBUG_MODULEP  
 Initialisieren und Verwenden der `m_pModule` Feld.  
  
 FIF_FUNCNAME_FORMAT  
 Formatiert den Namen der Funktion. Das Ergebnis wird zurückgegeben, der `m_bstrFunName` Feld und keine anderen Felder ausgefüllt wurden.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Fügt den Rückgabetyp zu den `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS  
 Fügt die Argumente für die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_LANGUAGE  
 Die Sprache, fügt die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_MODULE  
 Fügt den Modulnamen, um die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_LINES  
 Fügt die Anzahl von Zeilen, die die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_OFFSET  
 Hinzugefügt, die `m_bstrFuncName` Feld den Offset in Bytes vom Anfang der Zeile, wenn `FIF_FUNCNAME_LINES` angegeben ist. Wenn `FIF_FUNCNAME_LINES` nicht angegeben ist, oder wenn Zeilennummern nicht verfügbar sind, fügt den Offset in Bytes vom Beginn der Funktion.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Fügt den Typ jedes Arguments der Funktion, die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Fügt den Namen der einzelnen Argumente der Funktion, die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Fügt den Wert der einzelnen Argumente der Funktion, die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Fügt dem Typ, Name und Wert von allen Argumenten, die die `m_bstrFuncName` Feld.  
  
 FIF_ARGS_TYPES  
 Die Argumenttypen abgerufen und formatiert.  
  
 FIF_ARGS_NAMES  
 Die Argumentnamen abgerufen und formatiert.  
  
 FIF_ARGS_VALUES  
 Die Argumentwerte abgerufen und formatiert.  
  
 FIF_ARGS_ALL  
 Abzurufen Sie, und formatieren Sie den Typ, Name und Wert für alle Argumente.  
  
 FIF_ARGS_NOFORMAT  
 Gibt an, dass die Argumente sind nicht formatiert (z. B. nicht hinzufügen, öffnende und schließende Klammern um Argumentliste keine Trennzeichen zwischen Argumenten hinzufügen).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Gibt an, dass es sich bei funktionsauswertung (Eigenschaft) beim Abrufen der Werte für das Argument nicht verwendet werden soll.  
  
 FIF_FILTER_NON_USER_CODE  
 Die Debug-Engine wird nicht benutzerseitiger Codeframes zu filtern, damit sie nicht eingeschlossen werden.  
  
 FIF_ARGS_NO_TOSTRING  
 Erlauben Sie keine `ToString()` Funktion Auswertung oder formatieren, wenn Argumente der Funktion zurückgegeben.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Frame-Informationen sollten aus der gehosteten Anwendungsdomäne statt des hosting-Prozesses abgerufen werden.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden an übergeben die [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) und [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) Methoden, um anzugeben, welche Felder sind, initialisiert werden, in der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen.  
  
 Diese Flags werden auch verwendet, welche Felder der an die [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) -Struktur sind gültig und verwendet, wenn die Struktur zurückgegeben wird. Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
