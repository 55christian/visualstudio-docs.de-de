---
title: -ResetSettings (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a81c0082bc9b8e31c6c64ff1785f5f380709f3b5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650966"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Standardeinstellungen wieder her und startet die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] - IDE automatisch. Setzt die Einstellungen optional auf die einer angegebenen VSSETTINGS-Datei zurück.  
  
 Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zuerst gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumente  
 `SettingsFile`  
 Der vollständige Pfad und Name der VSSETTINGS-Datei, die auf [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] angewendet werden soll.  
  
 Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn kein `SettingsFile` angegeben ist, werden Sie beim nächsten Start von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aufgefordert, eine Standardauflistung von Einstellungen auswählen.  
  
## <a name="example"></a>Beispiel  
 In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
