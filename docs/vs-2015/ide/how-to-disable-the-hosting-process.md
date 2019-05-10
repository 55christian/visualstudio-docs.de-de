---
title: 'Vorgehensweise: Deaktivieren des Hostprozesses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92e4fb1ae7cf7acf387eb9387284534eb55c1066
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429924"
---
# <a name="how-to-disable-the-hosting-process"></a>Gewusst wie: Deaktivieren des Hostprozesses
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aufrufe an bestimmte APIs können beeinflusst werden, wenn der Hostprozesses aktiviert wird. In diesen Fällen ist es erforderlich, den Hostprozess zu deaktivieren, damit korrekte Ergebnisse zurückgegeben werden.  
  
### <a name="to-disable-the-hosting-process"></a>So deaktivieren Sie den Hostprozess  
  
1. Öffnen Sie ein ausführbares Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projekte, die keine ausführbare Dateien erzeugen (z. B. Klassenbibliothek- oder Dienstprojekte) verfügen über diese Option nicht.  
  
2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
3. Klicken Sie auf die Registerkarte **Debuggen**.  
  
4. Deaktivieren Sie das Kontrollkästchen **Visual Studio-Hostprozess aktivieren**.  
  
   Wenn der Hostprozess deaktiviert ist, sind mehrere Debugfeatures nicht verfügbar oder weisen eine eingeschränkte Leistung auf. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
   Generelle Einschränkungen bei deaktiviertem Hostprozess:  
  
- Die Vorlaufzeit bis zum Start des Debugvorgangs bei [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Anwendungen verlängert sich.  
  
- Die Ausdrucksauswertung zur Entwurfszeit ist nicht verfügbar.  
  
- Das Debuggen teilweise vertrauenswürdiger Anwendungen ist nicht möglich.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
 [Hostprozess („vshost.exe“)](../ide/hosting-process-vshost-exe.md)   
 [Builds während der Anwendungsentwicklung](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
