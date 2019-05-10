---
title: Elements (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff2071ba71d60db87332b0e23948d63ac1b2289
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845560"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (dynamische XElement-Eigenschaft)

Sucht nach einem Indexer, der zum Abrufen der untergeordneten Elemente des aktuellen Elements verwendet wird, die dem angegebenen erweiterten Namen entsprechen.

## <a name="syntax"></a>Syntax

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Indexer des Typs `IEnumerable<XElement> Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen des gewünschten untergeordneten Elements und gibt die passenden untergeordneten Elemente in einer <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`-Auflistung zurück.

## <a name="remarks"></a>Anmerkungen

Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName>-Methode der <xref:System.Xml.Linq.XContainer>-Klasse.

Die Elemente in der zurückgegebenen Auflistung sind in derselben Reihenfolge aufgeführt wie im XML-Quelldokument.

Diese Eigenschaft verwendet die verzögerte Ausführung.

## <a name="see-also"></a>Siehe auch

- [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Descendants](../designers/descendants-xelement-dynamic-property.md)