---
title: Verfügbarmachen von Ereignissen im Visual Studio SDK | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29fd9df90f58807ab3d48e077dcfa02d75eff837
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352601"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Verfügbarmachen von Ereignissen in Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Sie mithilfe der Automatisierung Ereignissen der Datenquelle. Es wird empfohlen, dass Sie Ereignisse für Projekte und Projektelemente Datenquelle.

 Ereignisse werden abgerufen, indem die Automatisierung von Kunden aus der <xref:EnvDTE.DTEClass.Events%2A> Objekt oder <xref:EnvDTE.DTEClass.GetObject%2A> (z. B. `GetObject("EventObjectName")`). Die Umgebung ruft `IDispatch::Invoke` mithilfe der `DISPATCH_METHOD` oder `DISPATCH_PROPERTYGET` Flags, die ein Ereignis zurück.

 Der folgende Prozess wird erläutert, wie die VSPackage-spezifisches Ereignisse zurückgegeben werden.

1. Die Umgebung wird gestartet.

2. Es liest aus der Registrierung alle Wertnamen unter der **Automation**, **AutomationEvents**, und **AutomationProperties** Schlüssel aller VSPackages und speichert die Namen in einer Tabelle.

3. In diesem Beispiel ruft ein automatisierungsbenutzer `DTE.Events.AutomationProjectsEvents` oder `DTE.Events.AutomationProjectItemsEvents`.

4. Die Umgebung sucht den Zeichenfolgenparameter in der Tabelle und lädt die entsprechende VSPackage.

5. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode mit dem Namen übergeben, in dem Aufruf; in diesem Beispiel `AutomationProjectsEvents` oder `AutomationProjectItemsEvents`.

6. Das VSPackage erstellt ein Stammobjekt, das Methoden, z. B. verfügt `get_AutomationProjectsEvents` und `get_AutomationProjectItemEvents` und gibt dann einen IDispatch-Zeiger auf das Objekt zurück.

7. Die Umgebung Ruft die entsprechende Methode, die anhand des Namens in das Automation-Aufruf übergeben.

8. Die `get_` Methode erstellt ein anderes IDispatch-basierte-Ereignisobjekt, das implementiert die `IConnectionPointContainer` Schnittstelle und die `IConnectionPoint` -Schnittstelle und gibt eine `IDispatchpointer` auf das Objekt.

   Um ein Ereignis verfügbar zu machen, mithilfe der Automatisierung, müssen Sie auf Antworten <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> und sehen Sie sich für die Zeichenfolgen, die Sie in der Registrierung hinzufügen. Im Beispiel Basic-Projekts die Zeichenfolgen sind *BscProjectsEvents* und *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Registrierungseinträge aus dem Basisprojekt-Beispiel
 Dieser Abschnitt zeigt, wo Sie Automation Ereigniswerte zur Registrierung hinzuzufügen.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = gibt die `AutomationProjectEvents` Objekt.

 **AutomationProjectItemEvents** = gibt die `AutomationProjectItemsEvents` Objekt.

|Name|Typ|Bereich|Beschreibung|
|----------|----------|-----------|-----------------|
|Standard (@)|REG_SZ|nicht verwendete|Nicht verwendet. Sie können das Datenfeld für die Dokumentation verwenden.|
|*AutomationProjectsEvents*|REG_SZ|Der Name des Ereignisobjekts.|Nur der Schlüsselname ist relevant. Sie können das Datenfeld für die Dokumentation verwenden.<br /><br /> Dieses Beispiel stammt aus dem Basisprojekt-Beispiel.|
|*AutomationProjectItemEvents*|REG_SZ|Name des Ereignisobjekts|Nur der Schlüsselname ist relevant. Sie können das Datenfeld für die Dokumentation verwenden.<br /><br /> Dieses Beispiel stammt aus dem Basisprojekt-Beispiel.|

 Wenn eines Ihrer Objekte von einem Consumer Automation angefordert werden, erstellen Sie ein Root-Objekt, das Methoden für alle Ereignisse enthält, die das VSPackage unterstützt. Die Umgebung Ruft die entsprechende `get_` Methode für dieses Objekt. Z. B. wenn `DTE.Events.AutomationProjectsEvents` aufgerufen wird, die `get_AutomationProjectsEvents` für das Stammobjekt-Methode wird aufgerufen.

 ![Visual Studio-Projekt-Ereignisse](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Automatisierungsmodell für Ereignisse

 Die Klasse `CProjectEventsContainer` stellt dar, das Quellobjekt für *BscProjectsEvents*, und `CProjectItemsEventsContainer` stellt dar, das Quellobjekt für *BscProjectItemsEvents*.

 In den meisten Fällen müssen Sie ein neues Objekt für jedes Ereignis-Anforderung zurückgeben, da die meisten Objekte ein Filterobjekt in Anspruch nehmen. Wenn Sie das Ereignis ausgelöst werden, überprüfen Sie diesen Filter, um sicherzustellen, dass der Ereignishandler aufgerufen wird.

 *AutomationEvents.h* und *AutomationEvents.cpp* enthält Deklarationen und Implementierungen der Klassen in der folgenden Tabelle.

|Klasse|Beschreibung|
|-----------|-----------------|
|`CAutomationEvents`|Implementiert ein Stamm Ereignisobjekt abgerufen, die von der `DTE.Events` Objekt.|
|`CProjectsEventsContainer` und `CProjectItemsEventsContainer`|Implementieren Sie die Ereignisobjekte für die Datenquelle, die die entsprechenden Ereignissen ausgelöst werden.|

 Im folgenden Codebeispiel wird veranschaulicht, eine Anforderung für ein Ereignisobjekt.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 Im obigen Code `g_wszAutomationProjects` ist der Name der Projektsammlung (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) und `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents* ) sind die Namen der Projektereignisse und Projektelemente Ereignisse, die aus der VSPackage-Implementierung erstellt werden.

 Ereignisobjekte werden abgerufen, von dem gleichen zentralen Standort, der `DTE.Events` Objekt. Auf diese Weise werden alle Ereignisobjekte gruppiert, damit Benutzer keine durchsuchen das gesamte Objektmodell um ein bestimmtes Ereignis zu suchen. Dadurch können Sie Ihre bestimmten VSPackage-Objekten, statt Sie Ihren eigenen Code für eine systemweite Ereignisse implementieren, bereitstellen. Jedoch für den Endbenutzer, die müssen finden Sie ein Ereignis für Ihre `ProjectItem` -Schnittstelle, es ist nicht sofort klar, von dem das Ereignisobjekt abgerufen wird.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
