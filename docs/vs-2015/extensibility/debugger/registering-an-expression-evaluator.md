---
title: Registrieren einer Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435678"
---
# <a name="registering-an-expression-evaluator"></a>Registrieren einer Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) muss sich als eine Klassenfactory mit der Windows-COM-Umgebung und die Visual Studio zu registrieren. Ein EE wird als DLL implementiert, so, dass es in den Adressraum des Debug-Engine (DE) oder des Visual Studio-Adressraums, je nachdem, welche Entität die EE instanziiert eingefügt werden kann.  
  
## <a name="managed-code-expression-evaluator"></a>Ausdrucksauswertung für verwalteten Code  
 EE wird als eine Klassenbibliothek, eine DLL handelt, der sich mit der COM-Umgebung, die Schritte in der Regel durch einen Aufruf der VSIP-Programm registriert implementiert mit verwaltetem Code **regpkg.exe**. Der tatsächliche Prozess des Schreibens von die Registrierungsschlüssel für die COM-Umgebung wird automatisch durchgeführt.  
  
 Eine Methode der Hauptklasse wird markiert, mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, gibt an, dass die Methode besteht darin, aufgerufen werden, wenn die DLL mit COM registriert wird Diese Registrierungsmethode, die häufig aufgerufen `RegisterClass`, führt die Aufgabe der Registrierung der DLL mit Visual Studio. Eine entsprechende `UnregisterClass` (mit markiert die <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), macht die Auswirkungen der `RegisterClass` Wenn die DLL wird deinstalliert.  
  
 Die gleichen Registrierungseinträge erfolgen wie bei einer EE in nicht verwaltetem Code geschrieben werden; der einzige Unterschied ist, dass es keine Hilfsfunktion wie z. B. `SetEEMetric` für die Arbeit für Sie. Ein Beispiel für diesen Prozess für die Registrierung/Aufhebung der Registrierung sieht folgendermaßen aus:  
  
### <a name="example"></a>Beispiel  
 Diese Funktion zeigt, wie eine EE für verwaltete Code registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Ausdrucksauswertung von nicht verwaltetem Code  
 Die EE-DLL implementiert die `DllRegisterServer` Funktion, um sich mit COM-Umgebung als auch Visual Studio zu registrieren.  
  
> [!NOTE]
> Die MyCEE Registrierung Codebeispiel wird in der Datei dllentry.cpp, finden Sie in der VSIP-Installation unter EnVSDK\MyCPkgs\MyCEE befindet sich.  
  
### <a name="dll-server-process"></a>DLL-Server-Prozess  
 Wenn Sie die EE, die DLL-Server zu registrieren:  
  
1. Registriert die Klassenfactory `CLSID` gemäß den normalen COM-Konventionen.  
  
2. Ruft die Hilfsfunktion `SetEEMetric` mit Visual Studio die EE-Metriken, die in der folgenden Tabelle gezeigt registrieren. Die Funktion `SetEEMetric` und die unten angegebenen Metriken sind Teil der dbgmetric.lib-Bibliothek. Finden Sie unter [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Details.  
  
    |Metrik|Beschreibung|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` der Factory EE-Klasse|  
    |`metricName`|Name des der EE als eine anzeigbare Zeichenfolge|  
    |`metricLanguage`|Der Namen der Sprache, die die EE ausgewertet werden soll|  
    |`metricEngine`|`GUID`s von der Debug-Engines (DE), die mit diesem EE arbeiten|  
  
    > [!NOTE]
    > Die `metricLanguage``GUID` identifiziert die Sprache von Namen, aber es ist die `guidLang` Argument `SetEEMetric` , bei dem die Sprache ausgewählt. Wenn der Compiler die Debuginformationsdatei generiert, sollten die entsprechenden schreiben `guidLang` , damit die DE weiß, welche EE verwenden. Die DE fordert den symbolanbieter in der Regel für diese Sprache `GUID`, die in der Debug-Informationsdatei gespeichert ist.  
  
3. Registriert bei Visual Studio erstellen, die Schlüssel unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X.Y* ist die Version von Visual Studio zu registrieren.  
  
### <a name="example"></a>Beispiel  
 Diese Funktion zeigt, wie eine nicht verwaltete Code (C++) EE registriert, und selbst mit Visual Studio hebt die Registrierung.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [SDK-Hilfsprogramme für das Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
