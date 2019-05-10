---
title: Schachteln von Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946957"
---
# <a name="nesting-projects"></a>Schachteln von Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Entwicklern von Unternehmensanwendungen, die das Visual Studio-Paket zu verwenden, können bequem gruppieren ähnliche Arten von Projekten, die zusammen in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit *Projekt Schachtelung*. Beispielsweise verwendet das Enterprise-Vorlagenprojekt geschachtelte Projekte zum Gruppieren von Projekten in Kategorien. Business-Fassade-Projekte, Web-UI-Projekte und usw. werden in einer Kategorie gruppiert.  
  
 In diesem Szenario gibt es keine Beschränkung der Anzahl der Projekte, die der Entwickler unter jedes übergeordneten Projekts, geschachtelt werden kann, auch wenn der Entwickler Grenzwerte programmgesteuert bereitstellen kann. Diese Art der Gruppierung kann auch rekursiv erfolgen in diesem Fall können die Projekte des gleichen Typs als ein untergeordnetes Projekt geschachtelt werden, unter das untergeordnete Element ein Unterprojekt des untergeordneten Elements, zu dem ein Unterprojekt des übergeordneten Elements ist.  
  
 Projekt Schachtelung ist nicht fester Bestandteil eines [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Sie müssen den Code zum Aktivieren der Schachtelung und Unterprojekt Schachtelung innerhalb von untergeordneten Projekten schreiben. Das übergeordnete Projekt ist eine spezielle VSPackage oder Projekttyp erstellt und registriert durch eine eigene GUID, die den Code, der erforderlich ist enthält, um die Schachtelung von Projekt zu implementieren.  
  
 Sie finden ein Beispiel für geschachtelte Projekte im Beispiel Example.Nested C#-Projekt.  
  
## <a name="nested-projects-example"></a>Beispiel für geschachtelte Projekte  
 ![Geschachtelte Projektmappen](../../extensibility/internals/media/vsnestedprojects.gif "VsNestedProjects")  
Beispiel für geschachtelte Projekte  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Implementieren von geschachtelten Projekten](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Überlegungen zum Entladen und Neuladen geschachtelte Projekte](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
