---
title: Generieren einer Dekonstruktorschnellaktion
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790314"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generieren eines Dekonstruktors in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Hiermit können Sie sofort den Methodenstub für einen neuen Dekonstruktor generieren.

**Hintergrund:** Wenn Sie Ihren Typ automatisch ordnungsgemäß dekonstruieren möchten.

**Vorteile**: Sie können einen Dekonstruktor manuell schreiben, mit diesem Feature wird der Stub jedoch mit den richtigen Out-Parametern für Sie generiert.

## <a name="generate-a-deconstructor"></a>Generieren eines Dekonstruktors

1. Deklarieren Sie einen neuen Typ mit den gewünschten Out-Parametern. Diese Deklaration löst einen Fehler aus, wenn keine Dekonstruktionsinstanz gefunden werden kann, die mit Ihrer Deklaration übereinstimmt.

   ![Fehler: fehlender Dekonstruktor](media/deconstruct.png)

2. Führen Sie einen der folgenden Schritte aus:

   - **Tastatur**
      - Drücken Sie mit dem Cursor in der Deklaration STRG+., um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
      - Klicken Sie auf das Symbol ![Schraubendrehersymbol](media/screwdriver.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der leeren Zeile in der Klasse platziert wurde.

      ![Codefix zum Generieren eines Dekonstruktors](media/deconstruct-codefix.png)

3. Klicken Sie auf **Generate method 'MyInternalClass.Deconstruct'** (Methode „MyInternalClass.Deconstruct“ generieren), um den Dekonstruktor zu generieren.

   ![Resultierender Dekonstruktorcode](media/deconstruct-result.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)