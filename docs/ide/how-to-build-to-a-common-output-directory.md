---
title: 'Vorgehensweise: Erstellen in einem gemeinsamen Ausgabeverzeichnis'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1e669789d2117b4bd2ee550dfffb147e46620c4
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416748"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Vorgehensweise: Erstellen in einem gemeinsamen Ausgabeverzeichnis

Standardmäßig erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jedes Projekt in einer Projektmappe in einem eigenen Ordner in der Projektmappe. Sie können die Buildausgabepfade Ihrer Projekte so ändern, dass alle Ausgaben im selben Ordner abgelegt werden.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>So legen Sie alle Ausgaben in einem gemeinsamen Verzeichnis ab

1. Klicken Sie auf ein Projekt in der Projektmappe.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

3. Klicken Sie je nach Art des Projekts auf die Registerkarte **Kompilieren** oder **Erstellen**, und legen Sie den **Ausgabepfad** für alle Projekte in der Projektmappe auf denselben Ordner fest.

4. Wiederholen Sie die Schritte 1 bis 3 für alle Projekte in der Projektmappe.

## <a name="see-also"></a>Siehe auch

- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
- [Vorgehensweise: Ändern des Buildausgabeverzeichnisses](../ide/how-to-change-the-build-output-directory.md)