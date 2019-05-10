---
title: VSCT-XML-Schemareferenz | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37b3f3105280ec384b6c180a65d2492ffd3bb02c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411116"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML-Schemareferenz
Bietet ein Befehl Tabelle Compiler-Schemaelemente, mit den zulässigen untergeordneten Elemente und Attribute für die einzelnen.

 Eine XML-basierten Befehl Tabelle-Konfigurationsdatei (VSCT) definiert die Befehlselemente, die ein VSPackage bereitstellt, die integrierte Entwicklungsumgebung (IDE). Zu diesen Elementen gehören die Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.

> [!NOTE]
> Der VSCT-Compiler kann einen Präprozessor auf die VSCT-Datei ausgeführt werden. Da dies in der Regel ist der C++-Präprozessor, Sie definieren können, enthält, und Makros, die haben der gleichen Syntax, die in C++-Dateien verwendet wird. Beispiele hierfür finden Sie in der VSCT-Datei, die die **neues Projekt** -Assistent erstellt für ein VSPackage-Projekt.

## <a name="optional-elements"></a>Optionale Elemente
 Einige VSCT-Elemente sind optional. Wenn eine `Parent` Argument nicht angegeben ist, Group_Undefined:0 wird implizit verwendet werden. Wenn ein `Icon` Argument nicht angegeben ist, wird GuidOfficeIcon:msotcidNoIcon abgeleitet werden. Wenn eine Tastenkombination definiert ist, ist die Emulation, die in der Regel nicht verwendet wird, optional.

 Bitmap-Elemente zum Zeitpunkt der Kompilierung eingebettet werden können, durch Angeben des Speicherorts für den bitmapstrip in die `href` Argument. Bitmapstrip wird kopiert, die während der Zusammenführung nicht aus den Ressourcen der DLL extrahiert. Wenn ein `href` Argument angegeben wird, die `usedList` Argument ist optional, und alle bereitstellungsslots im bitmapstrip gelten verwendet.

 Alle GUID und ID-Werte müssen mit symbolischen Namen definiert werden. Diese Namen können definiert werden, in den Headerdateien oder im VSCT \<Symbole > Abschnitte. Die symbolischen Namen müssen lokal sein und über enthalten \<Include >-Elemente oder \<"extern" > Elemente. Importiert ein symbolischer Namen aus einer Headerdatei angegeben werden, eine \<"extern" > Element, wenn das einfache Muster folgt #define SYMBOLWERT. Der Wert kann ein anderes Symbol sein, solange dieses Symbol zuvor definiert wurde. GUID-Definitionen, müssen der OLE- oder C++-Format entsprechen. ID-Werte möglicherweise Dezimalstellen oder hexadezimalen Ziffern, die 0 X vorangestellt werden, wie in den folgenden Zeilen dargestellt:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  XML-Kommentaren können verwendet werden, aber Round-Trip Tools der grafischen Benutzeroberfläche (GUI) verwerfen können. Der Inhalt des \<Annotation >-Elemente sind unabhängig vom Format beibehalten werden garantiert.

## <a name="schema-hierarchy"></a>Schemahierarchie
 Eine VSCT-Datei hat die folgenden wichtigen Elemente.

- [CommandTable-element](../extensibility/commandtable-element.md)

- [Extern-element](../extensibility/extern-element.md)

- [Include-element](../extensibility/include-element.md)

- [Definieren Sie element](../extensibility/define-element.md)

- [Commands-element](../extensibility/commands-element.md)

- [CommandPlacements-element](../extensibility/commandplacements-element.md)

- [VisibilityConstraints-element](../extensibility/visibilityconstraints-element.md)

- [KeyBindings-element](../extensibility/keybindings-element.md)

- [UsedCommands-element](../extensibility/usedcommands-element.md)

- [Übergeordnetes element](../extensibility/parent-element.md)

- [Icon-element](../extensibility/icon-element.md)

- [Strings-element](../extensibility/strings-element.md)

- [Commandflag-element](../extensibility/command-flag-element.md)

- [Symbols-element](../extensibility/symbols-element.md)

- [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Siehe auch
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)