---
title: MSBuild-Sonderzeichen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7af1f137624c0af1fce02fde524d7fb4178cbad
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65084057"
---
# <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserviert einige Zeichen für die besondere Verwendung in bestimmten Kontexten. Sie müssen diese Zeichen nur mit einem Escapezeichen versehen, wenn Sie sie in dem für sie reservierten Kontext in ihrer ursprünglichen Bedeutung verwenden möchten. Beispielsweise hat ein Sternchen nur in den Attributen `Include` und `Exclude` einer Elementdefinition und im Zusammenhang mit Aufrufen von `CreateItem` eine besondere Bedeutung. Wenn aber ein Sternchen in diesen Kontexten wirklich als Sternchen angezeigt werden soll, müssen Sie es mit einem Escapezeichen versehen. In allen anderen Kontexten müssen Sie lediglich auf die Sternchentaste drücken, wenn ein Sternchen angezeigt werden soll.

 Verwenden Sie die Syntax %\<xx>, um ein Sonderzeichen mit einem Escapezeichen zu versehen. Hierbei stellt \<xx> den Hexadezimalwert des ASCII-Zeichens dar. Weitere Informationen finden Sie unter [Vorgehensweise: Escapesonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Sonderzeichen
 In der folgenden Tabelle werden Sonderzeichen für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aufgeführt:

|**Zeichen**|**ASCII**|**Reservierte Nutzung**|
|-------------------|---------------|------------------------|
|%|%25|Verweisen auf Metadaten|
|$|%24|Verweisen auf Eigenschaften|
|@|%40|Verweisen auf Elementlisten|
|&#96;|%27|Bedingungen und andere Ausdrücke|
|;|%3B|Listentrennzeichen|
|?|%3F|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|
|*|%2A|Platzhalterzeichen für Dateinamen in `Include`- und `Exclude`-Attributen|

## <a name="see-also"></a>Siehe auch
- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
- [Elemente](../msbuild/msbuild-items.md)