---
title: Erstellen von Projektinstanzen mithilfe von Projektfactorys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f26b11aaf74b73535c82ebcd6422f3be0bba3f22
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697203"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Erstellen von Projektinstanzen mithilfe von Projektfactorys
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekttypen in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwenden eine *Projektzuordnungsinstanz* zum Erstellen von Instanzen von Project-Objekte. Eine Projektzuordnungsinstanz ähnelt einer standard-Klassenfactory für cocreatable COM-Objekte. Project-Objekte sind jedoch nicht cocreatable: sie können nur mit einer Projektfactory erstellt werden.  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE Ruft die Projekt-Factory, die in einem VSPackage implementiert werden, wenn ein Benutzer ein vorhandenes Projekt lädt oder ein neues Projekt in erstellt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Das neue Projektobjekt enthält die IDE mit genügend Informationen zum Auffüllen der Projektmappen-Explorer. Das neue Projektobjekt bietet auch die erforderlichen Schnittstellen für die Unterstützung aller relevanten UI-Aktionen, die von der IDE initiiert.  
  
 Sie können die implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle in einer Klasse in Ihrem Projekt. In der Regel befindet sich in ein eigenes Modul.  
  
 Ein Beispiel für die Implementierung von der `IVsProjectFactory` Benutzeroberfläche, siehe PrjFac.cpp, der in enthalten ist das [Basisprojekt](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) Beispielverzeichnis.  
  
 Projekte, die unterstützen, die aggregiert wird durch einen Besitzer müssen es sich um einen Besitzer-Schlüssel in der Projektdatei beibehalten. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Methode mit einem Besitzer-Schlüssel an einem Projekt aufgerufen wird, das besessenen Projekt konvertiert seinen Besitzer-Schlüssel in eine Projektzuordnungsinstanz GUID dann Ruft die `CreateProject` Methode für dieses Projekt-Factory die tatsächliche Erstellung zu tun.  
  
## <a name="creating-an-owned-project"></a>Erstellen eines Projekts im Besitz des Benutzers  
 Ein Besitzer erstellt ein Projekt im Besitz in zwei Phasen:  
  
1. Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Methode. Dies gibt dem besessenen Projekt eine Chance, erstellen Sie ein aggregiertes Projektobjekt auf Grundlage der Eingabe steuern `IUnknown`. Das Projekt im Besitz übergibt die innere `IUnknown` und des aggregierten Objekts wieder zum Projekt Besitzer. Dies gibt dem besessenen Projekt eine Möglichkeit zum Speichern von des inneren `IUnknown`.  
  
2. Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> Methode. Das Projekt im Besitz ist alle seine Instanziierung, wenn diese Methode, statt aufgerufen wird `IVsProjectFactory::CreateProject` wie bei Projekten, die nicht besitzt. Die Eingabe `VSOWNEDPROJECTOBJECT` Enumeration ist in der Regel im Besitz des Benutzers aggregierte Projekt. Das Projekt im Besitz kann diese Variable verwenden, um zu bestimmen, ob die Project-Objekt bereits erstellt wurde (Cookie nicht gleich NULL) bzw. (Cookie gleich NULL) erstellt werden muss.  
  
   Projekttypen werden durch eine eindeutige Projekt-GUID, ähnlich wie die CLSID des cocreatable COM-Objekt identifiziert. In der Regel Verarbeiten einer Factory projekthandles Erstellen von Instanzen der einen einzelnen Projekttyp, obwohl es möglich, dass ein Projekt-Factory ist mehr als ein Projekttyp-GUID.  
  
   Projekttypen sind eine bestimmte Dateinamenerweiterung zugeordnet. Wenn ein Benutzer versucht, eine vorhandene Projektdatei zu öffnen oder versucht, ein neues Projekt erstellen, indem Sie eine Vorlage zu klonen, verwendet die IDE die Erweiterung für die Datei um zu bestimmen, das entsprechende Projekt-GUID an.  
  
   Sobald die IDE stellt fest, ob es muss ein neues Projekt erstellen oder Öffnen ein vorhandenes Projekt eines bestimmten Typs, die IDE die Informationen in der Registrierung unter [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] verwendet, um die finden VSPackage implementiert die erforderliche Projekt-Factory. Die IDE wird dieses VSPackage geladen. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> -Methode, die VSPackages muss die Projekt-Factory mit der IDE registrieren, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> Methode.  
  
   Die primäre Methode für die `IVsProjectFactory` Schnittstelle ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> sollten die zwei Szenarien behandelt: Öffnen ein vorhandenes Projekt, und Erstellen eines neuen Projekts. Die meisten Projekte speichern ihren Projektzustand in einer Projektdatei. Neue Projekte werden in der Regel erstellt, durch Nutzung, die eine Kopie der Datei der Vorlage an die `CreateProject` -Methode, und öffnen Sie anschließend auf die Kopie. Vorhandene Projekte zur Instanziierung von werden direkt öffnen der Projektdatei übergeben `CreateProject` Methode. Die `CreateProject` Methode können zusätzliche Funktionen der Benutzeroberfläche angezeigt, für den Benutzer nach Bedarf.  
  
   Ein Projekt kann auch keine Dateien verwenden und stattdessen den Projektzustand in einem Speichermechanismus, als das Dateisystem, wie z. B. eine Datenbank oder Web-Server speichern. In diesem Fall der File-Name-Parameter übergeben, um die `CreateProject` Methode ist nicht tatsächlich einen Dateisystempfad jedoch eine eindeutige Zeichenfolge – eine URL, um die Projektdaten zu identifizieren. Sie müssen sich nicht um die Vorlagendateien kopieren, die übergeben werden `CreateProject` zum Auslösen der entsprechenden Konstruktionsreihenfolge ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
