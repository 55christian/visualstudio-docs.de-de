---
title: NameProfile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c2134c38a3910a5dd1308990b0788002a7ded2d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441900"
---
# <a name="nameprofile"></a>NameProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `NameProfile`-Funktion weist dem angegebenen Prozess oder Thread eine Zeichenfolge zu.  
  
 Die NameProfile-API ist nur für die Instrumentierungsprofilerstellung verfügbar. Die NameProfile-API wird für die Sampling-Profilerstellung nicht unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszName`  
  
 Der Name des Profilerstellungselements. Ein Name ist ungültig (wodurch NAME_ERROR_INVALID_NAME von NameProfileA zurückgegeben wird), wenn:  
  
- Der an NameProfileA übergebene Zeiger ein NULL-Wert ist  
  
- Die Zeichenfolgendaten von pszName mit einer Zahl beginnt  
  
- Die Zeichenfolgendaten von pszName einen Leerraum enthalten  
  
- Die Zeichenfolgendaten von pszName eines der folgenden Zeichen enthalten: ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>  
  
  `Level`  
  
  Gibt die Profilebene an, auf die die Sammlung von Leistungsdaten angewendet werden kann. Die folgenden **PROFILE_CONTROL_LEVEL**-Werte können verwendet werden, um eine der drei Ebenen anzugeben, auf die die Sammlung der Leistungsdaten angewendet werden kann:  
  
|Enumerator|Beschreibung|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Die Einstellung globaler Ebene wirkt sich auf alle Prozesse und Threads bei der Profilerstellung aus.|  
|PROFILE_PROCESSLEVEL|Die Einstellung auf die Prozessebene wirkt sich auf alle Threads aus, die Teil des angegebenen Prozesses sind.|  
|PROFILE_THREADLEVEL|Die Einstellung auf Threadebene der Profilerstellung wirkt sich auf den angegebenen Thread aus.|  
  
 `dwId`  
  
 Bezeichner der Profilerstellungsebene Verwenden Sie den Prozess- oder Threadbezeichner, der vom System generiert wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Die Funktion gibt mithilfe der **PROFILE_COMMAND_STATUS**-Enumeration einen Erfolg oder Fehler an. Einer der folgenden Werte kann zurückgegeben werden:  
  
|Enumerator|Beschreibung|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|Das angegebene Profilerstellungselement ist nicht vorhanden.|  
|NAME_ERROR_INVALID_NAME|Der Name ist ungültig.|  
|NAME_ERROR_LEVEL_NOEXIST|Die angegebene Profilebene ist nicht vorhanden.|  
|NAME_ERROR_NO_SUPPORT|Der angegebene Vorgang wird nicht unterstützt.|  
|NAME_ERROR_OUTOFMEMORY|Der Arbeitsspeicher war nicht verfügbar, um das Ereignis aufzuzeichnen.|  
|NAME_ERROR_REDEFINITION|Dem Profilelement wurde bereits ein Name zugewiesen. Der Name in dieser Funktion wird ignoriert.|  
|NAME_ERROR_TEXTTRUNCATED|Die Textlänge des Namens überschreitet 32 Zeichen inklusive des NULL-Zeichens und wurde daher gekürzt.|  
|NAME_OK|Der Name wurde erfolgreich registriert.|  
  
## <a name="remarks"></a>Anmerkungen  
 Jedem Prozess oder Thread kann nur ein Name zugewiesen werden. Nachdem ein Profilerstellungselement benannt wird, werden nachfolgende Aufrufe von NameProfile für dieses Element ignoriert.  
  
 Wenn verschiedenen Threads oder Prozessen der gleiche Name gegeben wird, enthält der Bericht die Daten aller Elemente auf dieser Ebene, die diesen Namen tragen.  
  
 Wenn Sie einen anderen Prozess oder Thread als den aktuellen angeben, müssen Sie sicherstellen, dass dieser initialisiert und gestartet wurde, bevor Sie diesen benennen. Andernfalls schlägt die NameProfile-Methode fehl.  
  
> [!IMPORTANT]
> Die API-Funktionen CreateProcess() und CreateThread() können Rückgaben liefern, bevor der Thread oder Prozess initialisiert wurde.  
  
## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Funktionsinformationen  
  
|||  
|-|-|  
|**Header**|Enthält VSPerf.h|  
|**Bibliothek**|Verwendet VSPerf.lib|  
|**Unicode**|Als `NameProfileW` (Unicode) und `NameProfileA` (ANSI) implementiert.|  
  
## <a name="example"></a>Beispiel  
 Der folgende Code stellt den Funktionsaufruf von NameProfile dar. In diesem Beispiel wird vorausgesetzt, dass die Win32-Zeichenfolgenmakros und die Compilereinstellungen für ANSI verwendet werden, um zu bestimmen, ob der Code die ANSI-Funktion abruft.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Profiler-APIs in Visual Studio (systemeigen)](../profiling/visual-studio-profiler-api-reference-native.md)
