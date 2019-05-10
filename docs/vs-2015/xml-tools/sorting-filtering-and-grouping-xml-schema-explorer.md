---
title: Sortieren, Filtern und gruppieren (XML-Schema-Explorer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c13f7c710e462e1edd45acbf68fa4642d3d422
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099441"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortieren, Filtern und Gruppieren (XML-Schema-Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die über die verfügbaren Optionen die **sortieren, Filtern und nachfolgend angezeigten Gruppierungsoptionen** Menü auf der Symbolleiste des XML-Schema-Explorer.  
  
## <a name="filter-options"></a>Filteroptionen  
 Die folgenden Filteroptionen sind verfügbar. In der Standardeinstellung die **Namespaces anzeigen** und **Schemadateien anzeigen** -Option aktiviert ist.  
  
- **Namespaces anzeigen**.  
  
- **Schemadateien anzeigen**.  
  
- **Compositors anzeigen (Sequence/Choice/All)**.  
  
## <a name="sorting-options"></a>Sortierungsoptionen  
 Die folgenden Sortierungsoptionen sind verfügbar. Der Standardwert ist **nach Sortiertyp**. Die "Sortieren nach"-Optionen gelten nicht für Dateien und Namespaces.  
  
- **Nach Typ sortieren**.  
  
- **Nach Namen sortieren**.  
  
- **Nach Dokumentreihenfolge**.  
  
### <a name="sort-by-type"></a>Nach Typ sortieren  
 Wenn die **nach Sortiertyp** Option ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert. Knoten sind innerhalb jeder Gruppe alphabetisch sortiert.  
  
1. `import`-Knoten  
  
2. `include`-Knoten  
  
3. `redefine`-Knoten  
  
4. `attribute`-Knoten  
  
5. `attributeGroup`-Knoten  
  
6. `complexType`-Knoten  
  
7. `simpleType`-Knoten  
  
8. `element`-Knoten  
  
9. `group`-Knoten  
  
### <a name="sort-by-name"></a>Nach Namen sortieren  
 Wenn die **nach Namen sortieren** Option ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert:  
  
1. `import`-Knoten (in alphabetischer Reihenfolge der Namespaces)  
  
2. `include`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)  
  
3. `redefine`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)  
  
4. Andere globale Knoten in alphabetischer Reihenfolge  
  
### <a name="document-order"></a>Dokumentreihenfolge  
 Die **Dokumentreihenfolge** Option ist verfügbar, wenn die **Schemadateien anzeigen** ausgewählt ist. Wenn **Dokumentreihenfolge** ausgewählt ist, werden globale Knoten in der Reihenfolge, in der sie in der Schemadatei vorkommen, angezeigt.  
  
## <a name="persisting-sortfilter-options"></a>Speichern von Sortierungs-/Filteroptionen  
 Die Sortierungs-, Filter- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.
