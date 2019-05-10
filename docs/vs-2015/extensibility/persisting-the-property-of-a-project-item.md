---
title: Beibehalten der Eigenschaft eines Projektelements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441544"
---
# <a name="persisting-the-property-of-a-project-item"></a>Beibehalten der Eigenschaft eines Projektelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie sollten eine Eigenschaft beibehalten werden, in denen Sie ein Projektelement, z. B. der Autor einer Quelldatei hinzu. Dies ist möglich, indem die Eigenschaft in der Projektdatei gespeichert.  
  
 Der erste Schritt beim Beibehalten einer Eigenschaft in einer Projektdatei zum Abrufen der Hierarchie des Projekts wird ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle. Sie können diese Schnittstelle abrufen, entweder mithilfe der Automatisierung oder mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Nachdem Sie die Schnittstelle abgerufen haben, können Sie es verwenden, um zu bestimmen, welche Projektelement derzeit ausgewählt ist. Nachdem Sie die Projekt-ID haben, können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> die Eigenschaft hinzugefügt.  
  
 In den folgenden Verfahren, die Sie beibehalten der Eigenschaft VsPkg.cs `Author` mit dem Wert `Tom` in der Projektdatei.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Um die Projekthierarchie, mit dem DTE-Objekt zu erhalten.  
  
1. Fügen Sie den folgenden Code zu Ihrem VSPackage an:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Die Projekt-Item-Eigenschaft mit dem DTE-Objekt beibehalten werden.  
  
1. Fügen Sie den folgenden Code, die den Code in der Methode im vorherigen Verfahren aus:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Zum Abrufen der Projekthierarchie IVsMonitorSelection verwenden  
  
1. Fügen Sie den folgenden Code zu Ihrem VSPackage an:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Die ausgewählten Projekt-Item-Eigenschaft beibehalten werden, erhalten der Teamprojekthierarchie  
  
1. Fügen Sie den folgenden Code, die den Code in der Methode im vorherigen Verfahren aus:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Um sicherzustellen, dass die Eigenschaft gespeichert wird  
  
1. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und öffnen oder erstellen Sie eine Lösung.  
  
2. Wählen Sie das Projekt VsPkg.cs im Element **Projektmappen-Explorer**.  
  
3. Verwenden Sie einen Haltepunkt, oder andernfalls zu bestimmen Sie, dass Ihr VSPackage geladen wird und SetItemAttribute ausgeführt wird.  
  
    > [!NOTE]
    > Können Sie Automatisches Laden eines VSPackages, in dem Benutzeroberflächenkontext <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
4. Schließen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , und klicken Sie dann die Projektdatei im Editor zu öffnen. Daraufhin sollte die \<Autor >-Tag mit dem Wert Tom, wie folgt:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Tools](../extensibility/internals/custom-tools.md)
