---
title: Registrieren eines Toolfensters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ef5cc84ea1fdce8e297d8b5bff6636065b3d044
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805783"
---
# <a name="register-a-tool-window"></a>Registrieren eines Toolfensters
Sie können die Toolfenster mit einer registrieren <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.

## <a name="example"></a>Beispiel

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Im obigen Code die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registriert die `PersistedWindowPane` und `DynamicWindowPane` Toolfenster in Visual Studio. Das persistente Toolfenster ist angedockt und im Registerkartenformat mit **Projektmappen-Explorer**, und das dynamische Fenster erhält ein Standardthema zum Starten von Position und Größe. Fenster Dynamische vorübergehend erfolgt, was bedeutet, dass er beim Starten nicht erstellt wird. Schreibt eine `DontForceCreate` Wert in der `ToolWindows` Schlüssel in der systemregistrierung. Weitere Informationen finden Sie unter [Tool-Fenster-Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).
