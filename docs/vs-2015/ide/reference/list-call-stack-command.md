---
title: Befehl „Aufrufliste auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 932dbc9e3971598748e462de92280ac7112f8c62
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665115"
---
# <a name="list-call-stack-command"></a>Befehl "Aufrufliste auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt die aktuelle Aufrufliste an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Dies ist optional. Legt den aktuellen Stapelrahmen fest, und zeigt keine Ausgabe an.  
  
## <a name="switches"></a>Schalter  
 Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.  
  
 /Count:`number` [oder] /C:`number`  
 Dies ist optional. Maximale Anzahl der anzuzeigenden Aufruflisten. Der Standardwert ist unbegrenzt.  
  
 /ShowTypes:`yes`|`no` [oder] /T:`yes`|`no`  
 Dies ist optional. Gibt an, ob Parametertypen angezeigt werden sollen. Der Standardwert ist `yes`sein.  
  
 /ShowNames:`yes`|`no` [oder] /N:`yes`|`no`  
 Dies ist optional. Gibt an, ob Parameternamen angezeigt werden sollen. Der Standardwert ist `yes`sein.  
  
 /ShowValues:`yes`|`no` [oder] /V:`yes`|`no`  
 Dies ist optional. Gibt an, ob Parameterwerte angezeigt werden sollen. Der Standardwert ist `yes`sein.  
  
 /ShowModule:`yes`|`no` [oder] /M:`yes`|`no`  
 Dies ist optional. Gibt an, ob der Modulname angezeigt werden soll. Der Standardwert ist `yes`sein.  
  
 /ShowLineOffset:`yes`|`no` [oder] /#:`yes`|`no`  
 Dies ist optional. Gibt an, ob der Zeilenoffset angezeigt werden soll. Der Standardwert ist `no`sein.  
  
 /ShowByteOffset:`yes`|`no` [oder] /B:`yes`|`no`  
 Dies ist optional. Gibt an, ob der Byte-Offset angezeigt werden soll. Der Standardwert ist `no`sein.  
  
 /ShowLanguage:`yes`|`no` [oder] /L:`yes`|`no`  
 Dies ist optional. Gibt an, ob die Sprache angezeigt werden soll. Der Standardwert ist `no`sein.  
  
 /IncludeCallsAcrossThreads:`yes`|`no` [oder] /I:`yes`|`no`  
 Dies ist optional. Gibt an, ob angegeben werden soll, ob andere Threads aufgerufen werden oder selbst aufrufen. Der Standardwert ist `no`sein.  
  
 /ShowExternalCode:`yes`|`no`  
 Dies ist optional. Gibt an, ob für die Aufrufliste nur Benutzercode angezeigt werden soll. Wenn die Funktion „Nur eigenen Code“ deaktiviert ist, wird der gesamte nicht benutzerseitige Code angezeigt. Wenn diese Funktion aktiviert ist, wird nicht benutzerseitiger Code als `[external]` in der Ausgabe der Aufrufliste angezeigt.  
  
 Thread:`n`  
 Dies ist optional. Zeigt die Aufrufliste für den Thread `n` an. Wenn kein Thread angegeben ist, wird die Aufrufliste für den aktuellen Thread angezeigt.  
  
## <a name="remarks"></a>Anmerkungen  
 Änderungen an den Argumenten oder Schaltern gelten bei zukünftigen Aufrufen dieses Befehls. Wenn Sie Debug.ListCallStackby selbst ausgeben, wird die gesamte Aufrufliste angezeigt. Wenn Sie beispielsweise einen Index angeben  
  
```  
Debug.ListCallStack 2  
```  
  
 wird der aktuelle Stapelrahmen auf diesen Frame festgelegt (in diesem Fall auf den zweiten Frame).  
  
 Sie können diesen Befehl auch mit dem vordefinierten Alias „kb“ schreiben. Sie können beispielsweise Folgendes eingeben:  
  
```  
kb 2  
```  
  
 um den aktuellen Stapelrahmen auf den zweiten Frame festzulegen.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl „Disassemblierung auflisten“](../../ide/reference/list-disassembly-command.md)   
 [Befehl „Threads auflisten“](../../ide/reference/list-threads-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
