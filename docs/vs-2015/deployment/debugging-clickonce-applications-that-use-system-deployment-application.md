---
title: Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187797"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Deployment können Sie konfigurieren, wie eine Anwendung aktualisiert wird. Wenn Sie zum verwenden und anpassen müssen jedoch erweiterte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungsfunktionen, Sie müssen auf das Bereitstellungsobjektmodell <xref:System.Deployment.Application>. Sie können die <xref:System.Deployment.Application> -APIs für erweiterte Aufgaben wie z. B.:  
  
- Erstellen eine Option "Jetzt aktualisieren" in Ihrer Anwendung  
  
- Bedingt, bedarfsgesteuerte downloads, von verschiedenen Anwendungskomponenten  
  
- Updates, die direkt in die Anwendung integriert  
  
- Garantiert, dass die Client-Anwendung immer auf dem neuesten Stand ist.  
  
  Da die <xref:System.Deployment.Application> APIs funktionieren nur, wenn eine Anwendung mit bereitgestellt wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Technologie, die einzige Möglichkeit, sie zu Debuggen ist, zum Bereitstellen der Anwendung mit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], hinzugefügt werden, und Debuggen. Es kann schwierig sein, den Debugger anfügen noch genügend Zeit, da dieser Code häufig ausgeführt wird, wenn die Anwendung gestartet und ausgeführt wird, bevor Sie den Debugger anfügen können. Eine Lösung besteht darin, Seitenumbrüche (oder beendet wird, für die Visual Basic-Projekte) vor Ihrer Update überprüfen oder auf Anforderung Code eingefügt werden sollen.  
  
  Die empfohlene Debuggen Verfahren lautet wie folgt aus:  
  
1. Bevor Sie beginnen, stellen Sie sicher, dass die Symboldateien (.pdb) und Quelldateien archiviert werden.  
  
2. Stellen Sie Version 1 der Anwendung.  
  
3. Erstellen einer neuen leeren Projektmappe an. Von der **Datei** Menü klicken Sie auf **neu**, klicken Sie dann **Projekt**. In der **neues Projekt** öffnen Sie im Dialogfeld die **andere Projekttypen** Knoten, wählen Sie dann die **Visual Studio-Projektmappen** Ordner. In der **Vorlagen** wählen Sie im Bereich **leere Projektmappe**.  
  
4. Fügen Sie den archivierten Quellspeicherort an den Eigenschaften für diese neue Lösung hinzu. In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, und klicken Sie auf **Eigenschaften**. In der **Eigenschaftenseiten** wählen Sie im Dialogfeld **Quelldateien debuggen**, fügen Sie dann das Verzeichnis mit den archivierten Quellcode hinzu. Andernfalls wird der Debugger veraltete Quelldateien an, gefunden werden, da es sich bei die quelldateipfaden in die PDB-Datei aufgezeichnet werden. Wenn der Debugger veraltete Quelldateien verwendet wird, sehen Sie eine Meldung angezeigt, die die Quelle nicht übereinstimmen.  
  
5. Stellen Sie sicher, dass der Debugger die PDB-Dateien finden kann. Wenn Sie diese mit Ihrer Anwendung bereitgestellt haben, wird der Debugger diese automatisch. Immer neben der Assembly betreffende zuerst gesucht. Andernfalls müssen Sie den Archivpfad zum Hinzufügen der **Symboldateien (.pdb) Orte für Symboldateien** (auf diese Option, die **Tools** Menü klicken Sie auf **Optionen**, öffnen Sie dann die  **Debuggen von** Knoten, und klicken Sie auf **Symbole**).  
  
6. Debuggen, was geschieht, zwischen den `CheckForUpdate` und `Download` / `Update` Methodenaufrufe.  
  
    Der Update-Code könnte beispielsweise folgendermaßen aussehen:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Stellen Sie Version 2.  
  
8. Es wurde versucht, den Debugger mit, um die Version 1 der Anwendung während des downloads ein Update für Version 2. Alternativ können Sie die `System.Diagnostics.Debugger.Break` Methode oder einfach `Stop` in Visual Basic. Natürlich sollten Sie nicht diese Methodenaufrufe in Produktionscode lassen.  
  
    Nehmen wir beispielsweise an, Sie Entwickeln einer Windows Forms-Anwendung, und Sie verfügen über einen Ereignishandler für diese Methode mit der Update-Logik, darin. Um dies zu debuggen, einfach anfügen, bevor die Schaltfläche gedrückt wird, und Sie einen Haltepunkt legen (Stellen Sie sicher, dass Sie die entsprechende archivierte Datei öffnen, und legen Sie den Haltepunkt vorhanden ist).  
  
   Verwenden der <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> Eigenschaft zum Aufrufen der <xref:System.Deployment.Application> APIs nur, wenn die Anwendung bereitgestellt wird; die APIs nicht aufgerufen werden soll während des Debuggens [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application>
