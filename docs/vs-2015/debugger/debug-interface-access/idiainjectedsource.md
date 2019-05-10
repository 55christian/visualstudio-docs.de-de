---
title: IDiaInjectedSource | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 59bd1cd56ee36c5e4164549df987f789aafe32e1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947518"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Greift auf eingefügt, in der DIA-Datenquelle gespeicherten Quellcodes.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaInjectedSource`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Ruft ab eine zyklische redundanzprüfung (CRC), der aus die Bytes des Quellcodes berechnet.|  
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Ruft die Anzahl der Bytes des Codes ab.|  
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Ruft den Dateinamen für die Quelle ab.|  
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Ruft ab, der Name der Objektdatei, unter dem die Quelle kompiliert wurde.|  
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Ruft den Namen keine Datei Quellcode; d. h. Code, der eingefügt wurde.|  
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Ruft den Indikator verwendeten Komprimierungstyp für die Datenquelle ab.|  
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Ruft die Quellbytes-Code ab.|  
  
## <a name="remarks"></a>Hinweise  
 Eingefügte Quelle ist Text, der während der Kompilierung eingefügt wird. Dies bedeutet jedoch nicht den Präprozessor `#include` in C++ verwendet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [idiaenuminjectedsources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) oder [idiaenuminjectedsources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) Methoden. Finden Sie unter den [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) Schnittstelle für ein Beispiel zum Abrufen von der `IDiaInjectedSource` Schnittstelle.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt die verfügbaren Daten aus der `IDiaInjectedSource` Schnittstelle. Ein alternativer Ansatz die Verwendung der [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) Benutzeroberfläche, siehe das Beispiel in der [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) Schnittstelle.  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
