---
title: Befehl „Symbolpfad“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27c4c8ac23e2524245107d9052642350e9db09d2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670396"
---
# <a name="symbol-path-command"></a>Befehl "Symbolpfad"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argumente  
 `pathname`  
 Dies ist optional. Ein durch Semikolons getrennte Liste der Pfade, in denen der Debugger nach Symbolen sucht.  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn kein `pathname` angegeben wird, werden von dem Befehl die aktuellen Symbolpfade aufgelistet.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden der Liste mit Symbolverzeichnissen zwei Pfade hinzugefügt.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine durch Semikolons getrennte Liste der aktuellen Symbolpfade angezeigt.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
