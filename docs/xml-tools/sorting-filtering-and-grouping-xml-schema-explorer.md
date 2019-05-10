---
title: Sortieren, Filtern und Gruppieren von im XML-Schema-Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740fd46d453a6e6a51285d418374d036d83bc598
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808105"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortieren, Filtern und gruppieren (XML-Schema-Explorer)

In diesem Thema wird beschrieben, die über die verfügbaren Optionen die **sortieren, Filtern und nachfolgend angezeigten Gruppierungsoptionen** Menü auf der **XML-Schema-Explorer** Symbolleiste.

## <a name="filter-options"></a>Filteroptionen

 Die folgenden Filteroptionen sind verfügbar. In der Standardeinstellung die **Namespaces anzeigen** und **Schemadateien anzeigen** -Option aktiviert ist.

- **Namespaces anzeigen**.

- **Schemadateien anzeigen**.

- **Compositors anzeigen (Sequence/Choice/All)**.

## <a name="sorting-options"></a>Sortieroptionen

 Die folgenden Sortierungsoptionen sind verfügbar. Der Standardwert ist **nach Sortiertyp**. **Sortieren nach** Optionen gelten nicht für Dateien und Namespaces.

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

## <a name="persisting-sortfilter-options"></a>Beibehalten von sortierungs-/Filteroptionen

 Die Sortierungs-, Filter- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.