---
title: Befehl „Threads auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90aff3fb3d3cbb596708bde1db8ff171198a5a60
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669120"
---
# <a name="list-threads-command"></a>Befehl "Threads auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt eine Liste der Threads im aktuellen Programm an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Dies ist optional. Wählt einen Thread nach seinem Index als aktuellen Thread aus  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn angegeben, kennzeichnet das `index`-Argument den angegebenen Thread als aktuellen Thread. Ein Sternchen (*) wird in der Liste neben dem aktuellen Thread angezeigt.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl „Aufrufliste auflisten“](../../ide/reference/list-call-stack-command.md)   
 [Befehl „Disassemblierung auflisten“](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
