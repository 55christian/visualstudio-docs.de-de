---
title: IDispatchEx-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3fd7d46fdcb1f3e86bddd53700d7bce6e21381
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000834"
---
# <a name="idispatchex-interface"></a>IDispatchEx-Schnittstelle
`IDispatchEx`, eine Erweiterung von der `IDispatch` angemessene-Schnittstelle, unterstützt die Funktionen, für dynamische Sprachen wie z. B. Skriptsprachen. In diesem Abschnitt wird beschrieben, die `IDispatchEx` Schnittstelle, die Unterschiede zwischen `IDispatch` und `IDispatchEx`, und die Gründe für die Erweiterungen. Es wird erwartet, dass Leser mit vertraut `IDispatch` und haben Zugriff auf die `IDispatch` Dokumentation.  
  
## <a name="remarks"></a>Hinweise  
 `IDispatch` für Microsoft Visual Basic wurde im Grunde entwickelt werden. Die primäre Einschränkung `IDispatch` besteht darin, dass es wird davon ausgegangen, dass Objekte statisch sind. Das heißt, da Objekte während der Laufzeit nicht geändert werden, kann Typinformationen vollständig diese zum Zeitpunkt der Kompilierung beschreiben. Dynamische Run-Time-Modelle, die in Skriptsprachen, z. B. Visual Basic Scripting Edition (VBScript) befinden und [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] und Objekt modelliert, z. B. Dynamic HTML erfordern eine flexiblere Schnittstelle.  
  
 `IDispatchEx` wurde entwickelt, um alle Dienste eines bieten `IDispatch` sowie einige Erweiterungen, die für dynamischere spät gebundene Sprachen wie z. B. Skriptsprachen geeignet sind. Die zusätzlichen Funktionen der `IDispatchEx` mehr `IDispatch` sind:  
  
- Neue Elemente hinzufügen, um ein Objekt ("Expando") – verwenden Sie `GetDispID` mit der `fdexNameEnsure` Flag.  
  
- Member eines Objekts zu löschen, verwenden Sie `DeleteMemberByName` oder `DeleteMemberByDispID`.  
  
- Groß-/Kleinschreibung Dispatch-Vorgänge – verwenden Sie `fdexNameCaseSensitive` oder `fdexNameCaseInsensitive`.  
  
- Suchen Sie nach dem Element mit impliziten Namen – verwenden Sie `fdexNameImplicit`.  
  
- Auflisten von DISPIDs eines Objekts – verwenden Sie `GetNextDispID`.  
  
- Zuordnung von DISPID zu Elementnamen – verwenden Sie `GetMemberName`.  
  
- Rufen Sie die Eigenschaften von objektmembern – verwenden Sie `GetMemberProperties`.  
  
- Methodenaufruf mit `this` Zeiger, verwenden Sie `InvokeEx` mit DISPATCH_METHOD.  
  
- Zulassen von Browsern mit Unterstützung für das Konzept von Namespaces, um die übergeordneten Namen Speicherplatz eines Objekts zu erhalten, verwenden Sie `GetNameSpaceParent`.  
  
  -Objekte zur Unterstützung `IDispatchEx` unterstützen möglicherweise auch `IDispatch` um Abwärtskompatibilität zu gewährleisten. Der dynamischen Natur der Objekte, die unterstützen `IDispatchEx` hat einige Auswirkungen auf die `IDispatch` Schnittstelle dieser Objekte. Z. B. `IDispatch` geht die folgenden Annahmen aus:  
  
- Das Element und der Parameter müssen für die Lebensdauer des Objekts DISPIDs konstant bleibt. Dadurch wird einen Client DISPIDs einmal erhalten und für die spätere Verwendung zwischenspeichern.  
  
  Da `IDispatchEx` ermöglicht das Hinzufügen und Löschen von Elementen, die den Satz von gültigen DISPIDs nicht konstant bleiben. Allerdings `IDispatchEx` erfordert, dass die Zuordnung zwischen DISPID und Membernamen konstant bleibt. Dies bedeutet, dass, wenn ein Element gelöscht wird:  
  
- Die DISPID kann nicht wiederverwendet werden, bis ein Element mit dem gleichen Namen erstellt wird.  
  
- Die DISPID muss für gültig bleiben `GetNextDispID`.  
  
- Die DISPID muss ordnungsgemäß akzeptiert werden, von einem der `IDispatch` oder `IDispatchEx` Methoden – sie müssen erkennen, wenn das Element gelöscht, und geben Sie einen geeigneten Fehlercode ("in der Regel DISP_E_MEMBERNOTFOUND" oder "S_FALSE") zurück.  
  
## <a name="examples"></a>Beispiele  
 Dies [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Code in der Funktion test() bewirkt Folgendes:  
  
- Erstellt ein neues Objekt durch Aufrufen der `Object` Konstruktor und weist einen Zeiger auf das neue Objekt an die Variable Obj.  
  
- Erstellt ein neues Element mit dem Namen Elem, in dem Objekt, und weist dieses Element einen Zeiger auf die Funktion Katze.  
  
- Ruft diese Funktion. Da es als eine Methode aufgerufen wird, wird die `this` Zeiger verweist auf das Objekt Obj. Die Funktion fügt ein neues Element, Balken, auf das Objekt.  
  
  Der vollständige HTML-Code ist:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Ein Steuerelement, das auf diesem gleichen Webseite platziert konnte einen Dispatch-Zeiger auf den Skript-Engines aus dem Browser abgerufen werden. Das Steuerelement könnte dann die Funktion test() implementieren:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Code aus dem Steuerelement, zu testen, ist das gleiche wie der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Funktion `test()`. Beachten Sie, dass diese Dispatch-Aufrufe, in der ausgeführten ausgeführt werden [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -engine und der Zustand der Engine zu ändern:  
  
- Ruft die Dispatch-Zeiger auf die Cat-Funktion mit `GetDispID()`.  
  
- Ruft die Dispatch-Zeiger auf das Objekt mit `GetDispID()`.  
  
- Erstellt ein Objekt durch Aufrufen der Funktion des Objekts mit `InvokeEx()` und erhält einen Dispatch-Zeiger auf das neu erstellte Objekt.  
  
- Erstellt ein neues Element, Elem, in das Objekt mit `GetDispID()` mit der `fdexNameEnsure` Flag.  
  
- Legt die Dispatch-Zeiger in Katze, in dem Element mit `InvokeEx()`.  
  
- Ruft die Dispatch-Zeiger, Cat als Methode durch Aufrufen von `InvokeEx()` und übergeben Sie die Dispatch-Zeiger auf das erstellte Objekt als die `this` Zeiger.  
  
- Die Cat-Methode erstellt ein neues Element, Balken, auf dem aktuellen `this` Objekt.  
  
- Überprüft, ob das neue Element wurde, die erstellt, in das erstellte Objekt durch Auflisten der Elemente, die mit `GetNextDispID()`.  
  
  Der Code für das Teststeuerelement:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Methoden  
 [IDispatchEx-Methode](../../winscript/reference/idispatchex-methods.md)