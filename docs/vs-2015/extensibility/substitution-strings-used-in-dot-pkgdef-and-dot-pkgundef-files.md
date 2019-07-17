---
title: Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160537"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>In PKGDEF- und PKGUNDEF-Dateien verwendete Ersetzungszeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die unten aufgeführten, in der PKGDEF Ersatzzeichenfolgen verwenden und pkgundef-Dateien, die Sie definieren, für Visual Studio isolierte Shell-Anwendung.  
  
## <a name="substitution-strings"></a>Ersetzen von Zeichenfolgen  
  
|Zeichenfolge|Beschreibung|  
|------------|-----------------|  
|$=*RegistryEntry*$|Der Wert des der *RegistryEntry* Eintrag. Wenn die Zeichenfolge für die Registrierung in einem umgekehrten Schrägstrich endet (\\), und klicken Sie dann den Standardwert des Registrierungsunterschlüssels verwendet wird. Z. B. die Ersetzung $ string = HKEY_CURRENT_USER\Environment\TEMP$ wird in den temporären Ordner des aktuellen Benutzers erweitert.|  
|$AppName$|Der qualifizierte Name der Anwendung, die an Einstiegspunkte AppEnv.dll übergeben wird. Der qualifizierte Name besteht aus den Namen der Anwendung, einem Unterstrich und den Klassenbezeichner (CLSID) des Automatisierungsobjekts Anwendung, der auch als Wert für die ThisVersionDTECLSID-Einstellung in der PKGDEF-Datei des Projekts aufgezeichnet wird.|  
|$AppDataLocalFolder|Der Unterordner unter % LocalAppData% für diese Anwendung.|  
|$BaseInstallDir$|Der vollständige Pfad des Speicherorts, wo Visual Studio installiert wurde.|  
|$CommonFiles$|Der Wert des der Variable %CommonProgramFiles%-Umgebung.|  
|$MyDocuments$|Der vollständige Pfad des Ordners "Eigene Dateien" des aktuellen Benutzers.|  
|$PackageFolder$|Der vollständige Pfad des Verzeichnisses, das die Paketdateien für die Assembly für die Anwendung enthält.|  
|$ProgramFiles$|Der Wert der Umgebungsvariablen % ProgramFiles %.|  
|$RootFolder$|Der vollständige Pfad des Stammverzeichnisses der Anwendung.|  
|$RootKey$|Der Stamm-Registrierungsschlüssel für die Anwendung. Der Stamm befindet sich standardmäßig HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (Wenn die Anwendung ausgeführt wird, _Config wird mit diesem Schlüssel angefügt). Es wird festgelegt, durch den RegistryRoot-Wert in der *SolutionName*PKGDEF-Datei.<br /><br /> Die $RootKey$ Zeichenfolge kann verwendet werden, um einen Registrierungswert unter dem Anwendungsunterschlüssel abzurufen. Z. B. die Zeichenfolge "$= $RootKey \AppIcon$" wird der Wert des Eintrags AppIcon unter dem Unterschlüssel der Anwendung Stamm zurückgegeben.<br /><br /> Der Parser die PKGDEF-Datei sequenziell verarbeitet und kann einen Registrierungseintrag unter dem Anwendungsunterschlüssel zugreifen, nur dann, wenn der Eintrag zuvor definiert wurde|  
|$ShellFolder$|Der vollständige Pfad des Speicherorts, wo Visual Studio installiert wurde.|  
|$System$|Der Ordner "Windows\System32".|  
|$WINDIR$|Der Windows-Ordner.|  
  
 Wenn der Parser die Ersatzzeichenfolge nicht erkennt, oder es kann nicht den Wert einen entsprechenden Registrierungseintrag oder Umgebungsvariable bestimmen, und klicken Sie dann auf diesen Teil der Zeichenfolge keine Ersetzung ausgeführt wird.
