---
title: Isolierte Shell-Einstiegspunktparameter (C++) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439810"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolierte Shell-Einstiegspunktparameter (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine Visual Studio Shell-basierten Anwendung startet, ruft er den Einstiegspunkt der Start von Visual Studio Shell. Die folgenden Einstellungen können im Aufruf an den Einstiegspunkt der Start der Shell überschrieben werden. Eine Beschreibung der einzelnen Einstellungen, finden Sie unter [. PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Die Visual Studio Shell Isolated-Vorlage erstellt eine Quelldatei *SolutionName*cpp, in denen *SolutionName* ist für die Anwendung der Namen der Projektmappe. Diese Datei definiert den Haupteinstiegspunkt für die Anwendung, die _tWinMain-Funktion. Diese Funktion ruft den Einstiegspunkt der Start der Shell.  
  
  Sie können das Verhalten der Anwendung ändern, indem Sie diese Einstellungen zu ändern, beim Starten der Anwendung.  
  
## <a name="parameters"></a>Parameter  
 Der Einstiegspunkt der Start von Visual Studio Shell definiert fünf Parameter. Ändern Sie die ersten vier Parameter nicht. Der fünfte Parameter akzeptiert eine Liste der Einstellungen außer Kraft setzen. Der Einstiegspunkt der Start der Shell wird von der Haupteinstiegspunkt einer Anwendung aufgerufen.  
  
 Der Einstiegspunkt der Start der Shell weist folgende Signatur auf.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Überschreiben Sie Parameter als ein null-Zeiger, wenn Sie nicht möchten, sollten Sie den Wert der Einstellungen zum Überschreiben alle Anwendungseinstellungen.  
  
 Um eine oder mehrere Einstellungen zu überschreiben, übergeben Sie eine Unicode-Zeichenfolge mit den Einstellungen außer Kraft gesetzt werden. Die Zeichenfolge ist eine durch Semikolons getrennte Liste von Name / Wert-Paaren. Jedes Paar enthält den Namen der Einstellung, um zu überschreiben, gefolgt von einem Gleichheitszeichen (=), gefolgt vom Wert der Einstellung angewendet wird.  
  
> [!NOTE]
> Nehmen Sie Leerzeichen nicht in der Unicode-Zeichenfolgen aus.  
  
 Für boolesche Einstellungen stehen für die folgenden Zeichenfolgen den Wert True; Alle anderen Zeichenfolgen darstellen, den Wert "false". Diese Zeichenfolgen werden Groß-/Kleinschreibung.  
  
- \+  
  
- 1  
  
- -1  
  
- an  
  
- true  
  
- ja  
  
## <a name="example"></a>Beispiel  
 Um-add-ins deaktivieren, und Ändern des Standardspeicherorts für Projekte für Ihre Anwendung, können Sie die letzten Parameter für "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp" festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md)   
 [PKGDEF-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
