---
title: 'Vorgehensweise: Programmgesteuerte Suche in einem bestimmten Ordner'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961900"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Vorgehensweise: Programmgesteuerte Suche in einem bestimmten Ordner
  Dieses Codebeispiel verwendet die `Find` und `FindNext` Methoden, um nach Text in der Betreffzeile von e-Mail-Nachrichten zu suchen, die in der **Posteingang**. Diese Methode verwendet eine Zeichenfolge um zu prüfen, der Buchstabe T Zeichenfolgenfilter ab, der die `Subject` Text.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
