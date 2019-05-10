---
title: Benutzerdefinierte Parameter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e86c2f48365f93c924b15ae8d696d53d3f4bb16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861274"
---
# <a name="custom-parameters"></a>Benutzerdefinierte Parameter
Benutzerdefinierte Parameter steuern den Betrieb des einen Assistenten, nachdem ein Assistent gestartet wurde. Eine verknüpfte *VSZ* Datei bietet eine Reihe von benutzerdefinierten Parametern, die von der integrierten Entwicklungsumgebung (IDE) verpackt und an den Assistenten als ein Array von Zeichenfolgen übergeben wird, wenn der Assistent gestartet wird. Der Assistent analysiert das Array von Zeichenfolgen und verwendet die Informationen zum Steuern der tatsächlichen Ausführung des Assistenten. Auf diese Weise kann ein Assistenten anpassen, Funktionen, die abhängig vom Inhalt der *VSZ* Datei.

 Kontextparameter, definieren den Zustand des Projekts auf der anderen Seite, beim Starten des Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).

 Es folgt ein Beispiel für eine *VSZ* -Datei mit benutzerdefinierten Parametern:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Der Autor der *VSZ* Datei fügt die Werte der Parameter hinzu. Wenn ein Benutzer auswählt **neues Projekt** oder **neues Element hinzufügen** auf die **Datei** Menü oder per Rechtsklick auf ein Projekt in **Projektmappen-Explorer**, der IDE erfasst die folgenden Werte in ein Array von Zeichenfolgen. Die IDE ruft dann des Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> -Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag Satz und die projektaufrufe der <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> -Methode, die für den Assistenten auszuführen und das Ergebnis zuständig ist.

 Der Assistent ist verantwortlich für das Array von Zeichenfolgen zu analysieren und, die auf die Zeichenfolgen entsprechend. Auf diese Weise können Sie durch die Implementierung von benutzerdefinierter Parameters einen Assistenten erstellen, die eine Vielzahl von Funktionen ausführt. Das heißt, ein Assistent möglicherweise drei verschiedene *VSZ* Dateien. Jede Datei werden verschiedene Sätze von benutzerdefinierten Parametern zum Steuern des Verhaltens des Assistenten in verschiedenen Situationen übergeben.

 Weitere Informationen finden Sie unter [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)