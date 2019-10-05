---
title: -Out („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e1f20b446d355ea0cbc6700de5f2e6f79de51d09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187879"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt eine Datei an, die Fehler speichern und anzeigen soll, wenn Sie eine Projektmappe ausführen, erstellen, erneut erstellen oder bereitstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argumente  
 `FileName`  
 Erforderlich. Der Pfad und der Name der Datei, die beim Erstellen einer ausführbaren Datei Fehler empfangen soll.  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn ein nicht vorhandener Dateiname angegeben wird, wird die Datei automatisch erstellt. Wenn die Datei bereits vorhanden ist, werden die Ergebnisse an die vorhandenen Inhalte der Datei angefügt.  
  
 Buildfehler in der Befehlszeile werden im **Befehlsfenster** und der Solution Builder-Ansicht des **Ausgabefensters** angezeigt. Diese Option erweist sich als nützlich, wenn Sie unbeaufsichtigte Builds ausführen und die Ergebnisse benötigen.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird `MySolution` ausgeführt, und es werden Fehler in die `MyErrorLog.txt`-Datei geschrieben.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [/Run („devenv.exe“)](../../ide/reference/run-devenv-exe.md)   
 [/Build („devenv.exe“)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
