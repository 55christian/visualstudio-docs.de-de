---
title: SccAddFromScc-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccf3a25bda14cf98fdba4a58b0032444badc4c4a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432493"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ermöglicht es dem Benutzer nach Dateien suchen, die bereits in der Quellcode-Verwaltungssystems sind, und stellen anschließend diese Dateien Teil des aktuellen Projekts. Diese Funktion kann z. B. eine allgemeinen Headerdatei in das aktuelle Projekt erhalten, ohne die Datei zu kopieren. Zurückgegebenen Array von Dateien mit `lplpFileNames`, enthält die Liste der Dateien, die der Benutzer möchte die IDE-Projekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpnFiles  
 [in, out] Ein Puffer für die Anzahl der Dateien, die in hinzugefügt werden. (Dies ist `NULL` , wenn der Arbeitsspeicher, zeigt `lplpFileNames` aufgehoben werden soll. Einzelheiten finden Sie unter "Hinweise".)  
  
 lplpFileNames  
 [in, out] Ein Array von Zeigern auf die Dateinamen ohne Verzeichnispfade. Dieses Array ist reserviert und freigegeben, indem das Quellcodeverwaltungs-Plug-in. Wenn `lpnFiles` = 1 und `lplpFileNames` nicht `NULL`, dem Vornamen in das Array verweist `lplpFileNames` den Zielordner enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Dateien wurden erfolgreich gespeichert und dem Projekt hinzugefügt.|  
|SCC_I_OPERATIONCANCELED|Vorgang abgebrochen hat keine Auswirkungen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird von die IDE aufgerufen. Wenn das Quellcodeverwaltungs-Plug-in einen lokalen Ordner angeben unterstützt, übergibt die IDE `lpnFiles` = 1, und übergibt den Namen des lokalen Ordners, in `lplpFileNames`.  
  
 Bei der der Aufruf von der `SccAddFromScc` Funktion zurückgibt, die das plug-in hat Werte zugeordnet `lpnFiles` und `lplpFileNames`, die speicherbelegung für das Array des Datei-Namen nach Bedarf (Beachten Sie, dass diese Zuweisung den Zeiger ersetzt `lplpFileNames`). Das Quellcodeverwaltungs-Plug-in ist verantwortlich für alle Dateien platzieren, in das Verzeichnis des Benutzers oder im Ordner angegebenen Bezeichnung. Die IDE werden die Dateien dann die IDE-Projekt hinzugefügt.  
  
 Zum Schluss die IDE ruft diese Funktion ein zweites Mal übergebe `NULL` für `lpnFiles`. Dies wird als eine spezielle Signal interpretiert, durch das Quellcodeverwaltungs-Plug-in die Speichermenge für das Array von Dateinamen in release `lplpFileNames``.`  
  
 `lplpFileNames` ist eine `char ***` Zeiger. Das Quellcodeverwaltungs-Plug-in wird einen Zeiger auf ein Array von Zeigern auf den Dateinamen, und daher die Liste auf die übliche Weise für diese API übergeben.  
  
> [!NOTE]
> Anfängliche Versionen der API VSSCI hat keine Möglichkeit, das Zielprojekt für die hinzugefügten Dateien anzugeben bereitgestellt. Um die Semantik der entsprechend den `lplpFIleNames` Parameter wurden verbessert, um ein in/Out-Parameter und nicht als Output-Parameter zu erleichtern. Wenn nur eine einzelne Datei angegeben ist, d. h. der Wert verweist `lpnFiles` = 1, und klicken Sie dann auf das erste Element der `lplpFileNames` wird der Zielordner enthält. Diese neue Semantik, die IDE-Aufrufe verwenden die `SccSetOption` -Funktion mit den `nOption`Parametersatz zu `SCC_OPT_SHARESUBPROJ`. Wenn ein Quellcodeverwaltungs-Plug-in die Semantik nicht unterstützt, gibt es zurück `SCC_E_OPTNOTSUPPORTED`. Tun dies der Fall ist, deaktiviert die Verwendung von der **hinzufügen, aus der Quellcodeverwaltung** Feature. Wenn eine-Plug-in unterstützt die **hinzufügen, aus der Quellcodeverwaltung** Feature (`SCC_CAP_ADDFROMSCC`), müssen sie unterstützen die neue Semantik und zurückgeben `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
