---
title: Registrieren der Befehlshandler von Interop-Assembly | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b07f018a35874e2ffc3f3be825abb227f2996aea
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425457"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrieren der Befehlshandler von Interop-Assemblys
Eine VSPackage muss zaregistrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit die integrierte Entwicklungsumgebung (IDE) seine Befehle ordnungsgemäß weiterleitet.

 Die Registrierung kann entweder durch die manuelle Bearbeitung oder über eine Registrierungsstelle (.rgs)-Datei aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Das Managed Package Framework (MPF) stellt diese Funktionalität über die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Klasse.

- [Tabelle Formatreferenz für Blobüberwachungsprotokolle Befehl](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) Ressourcen befinden sich im nicht verwalteten Satelliten-UI-Dlls.

## <a name="command-handler-registration-of-a-vspackage"></a>Befehl Registrierung von VSPackages
 Ein VSPackage als einen Handler für die Benutzeroberfläche (UI)-Basis Befehle erfordert einen Registrierungseintrag Namens nach dem VSPackage `GUID`. Dieser Registrierungseintrag gibt den Speicherort der Ressourcendatei für die VSPackage Benutzeroberfläche und die Menüressource innerhalb dieser Datei an. Der Registrierungseintrag selbst befindet sich unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version >* \Menus, wobei  *\<Version >* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 9.0.

> [!NOTE]
> Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann überschrieben werden, mit einer alternativen Stamm, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Shell initialisiert wird. Weitere Informationen zu den Stammpfad, finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Der Registrierungseintrag für CTMENU-Ressource
 Die Struktur des Registrierungseintrags lautet:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> ist der `GUID` des VSPackage in der Form {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Informationen zur Ressource >* besteht aus drei Elementen, die durch Kommas getrennt. Diese Elemente sind in der Reihenfolge auf:

 \<*Pfad zur Ressourcen-DLL*>, \< *Menü-Ressourcen-ID*>, \< *Menü-Version*>

 Die folgende Tabelle beschreibt die Felder der \< *Ressourceninformationen*>.

| Element | Beschreibung |
|---------------------------| - |
| \<*Pfad zur Ressourcen-DLL*> | Dies ist der vollständige Pfad zu den Ressourcen-DLL, die die Menüressource enthält oder diese leer gelassen, gibt an, dass die VSPackage Ressource DLL ist, verwendet werden (gemäß des Unterschlüssels "Pakete", in das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, die dieses Feld leer lassen. |
| \<*Menü-Ressourcen-ID*> | Dies ist die Ressourcen-ID der `CTMENU` Ressource, die alle Elemente der Benutzeroberfläche für das VSPackage enthält, wie vom kompiliert einen [VSCT](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) Datei. |
| \<*Menu Version*> | Dies ist eine Zahl, die als einer Version für die `CTMENU` Ressource. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet diesen Wert um zu bestimmen, ob er den Inhalt der erneutes zusammenführen muss die `CTMENU` Ressource mit dem Cache aller `CTMENU` Ressourcen. Ein erneutes Zusammenführen wird ausgelöst, durch den Devenv-Setup-Befehl ausführen.<br /><br /> Dieser Wert sollte zunächst auf 1 festgelegt und nach jeder Änderung erhöht die `CTMENU` Ressource und vor der erneutes zusammenführen. |

### <a name="example"></a>Beispiel
 Hier ist ein Beispiel für eine Reihe von Ressourceneinträgen:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Siehe auch
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)