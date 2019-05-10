---
title: VBArray erwartet. | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005991"
---
# <a name="vbarray-expected"></a>VBArray erwartet
Sie haben angegeben, ein Objekt, das eine Visual Basic-SafeArray nicht war, wurde erwartet.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Die SafeArray-Argument ist ein VBArray-Wert und muss einen VBArray-Wert abgerufen haben, vor der Übergabe an die `VBArray` Konstruktor. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, übergeben Sie nur **VBArray** Objekte die **VBArray** Konstruktor.  
  
## <a name="see-also"></a>Siehe auch  
 [VBArray-Objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)