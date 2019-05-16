---
title: -ResetAddin (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6321433b506d41df57150b5a135a800a16cef0ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689681"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Entfernt Befehle und die Befehlsbenutzeroberfläche, die dem angegebenen Add-In zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumente  
 `AddIn`  
 Dies ist optional. Der Befehlsname des Add-Ins.  
  
## <a name="remarks"></a>Anmerkungen  
 Standardmäßig entspricht der Befehlsname des Add-Ins *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em> und wird in Connect.cs als `commandName`-Parameter der `Exec`-Methode angezeigt. Sie können den Befehlsnamen auch überprüfen, indem Sie den Namen des Add-Ins im Befehlsfenster von Visual Studio eingeben und die Eingabe von IntelliSense vervollständigen lassen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird Visual Studio gestartet. Die Ausführung des Add-Ins `MyAddin` beim Starten wird verhindert.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
