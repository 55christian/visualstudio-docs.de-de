---
title: Verwalten von mehreren Threads in verwaltetem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e7198623283fa3ef9c82d6a39a1f7c1db6c760c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433052"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Verwalten von mehreren Threads in verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine verwaltete VSPackage-Erweiterung, die asynchrone Methoden aufrufen oder Vorgänge, die auf anderen Threads als dem Visual Studio-UI-Thread ausgeführt wurde verfügen, sollten Sie die folgenden Richtlinien befolgen. Sie können den UI-Thread reaktionsfähig halten, da muss nicht warten, Arbeit auf einem anderen Thread abgeschlossen. Sie können Ihren Code effizienter, vornehmen, da Sie nicht über zusätzliche Threads verfügen, die Stapelspeicherplatz einnehmen, und können Sie es machen, zuverlässiger und einfacher zu debuggen, da Sie, Deadlocks und Blockaden vermeiden.  
  
 Sie können im Allgemeinen vom UI-Thread wechseln, zu einem anderen Thread aus, oder umgekehrt. Bei der Rückgabe der Methode ist der aktuelle Thread der Thread, von dem es ursprünglich aufgerufen wurde.  
  
> [!IMPORTANT]
> Die folgenden Richtlinien verwenden Sie die APIs in der <xref:Microsoft.VisualStudio.Threading> Namespace, insbesondere die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Erhalten Sie eine Instanz von einem <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> aus der <xref:Microsoft.VisualStudio.Shell.ThreadHelper> Eigenschaft `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Wechseln Sie von der UI-Thread in einem Hintergrundthread  
  
1. Wenn Sie auf der UI-Thread und asynchronen Arbeit in einem Hintergrundthread möchten, verwenden Sie Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. Wenn Sie die UI-Thread und synchron blockiert, während Sie arbeiten in einem Hintergrundthread, Verwendung durchführen möchten die <xref:System.Threading.Tasks.TaskScheduler> Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Der Wechsel von einem Hintergrundthread zum UI-Thread  
  
1. Wenn Sie in einem Hintergrundthread und etwas der UI-Thread verwendet werden sollen <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Sie können die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Methode, um zum UI-Thread zu wechseln. Diese Methode sendet eine Meldung an den UI-Thread mit der Fortsetzung der aktuellen asynchronen Methode, und zudem kommuniziert er mit dem Rest von threading Framework legen Sie die richtige Priorität und Deadlocks zu vermeiden.  
  
     Wenn die Hintergrund-Thread-Methode nicht asynchron ist und Sie können nicht sie asynchrone, können Sie dennoch verwenden die `await` Syntax, um zum UI-Thread zu wechseln, indem Sie die Arbeit mit wrapping <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, wie in diesem Beispiel:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
