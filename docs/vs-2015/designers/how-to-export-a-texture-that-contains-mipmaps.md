---
title: 'Vorgehensweise: Exportieren einer Textur, die Mipmaps enthält | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f525f4b31a3535f6ea7b89d0443402240365cc7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159435"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Vorgehensweise: Exportieren einer Textur, die Mipmaps enthält
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Bildinhaltspipeline können Mipmaps aus einem Quellbild als Teil der Buildphase des Projekts generiert werden. Wenn Sie den Bildinhalt jeder MIP-Ebene nicht manuell angeben müssen (wie es bei bestimmten Effekten der Fall ist) stellt das Generieren von Mipmaps zur Buildzeit sicher, dass Mipmapinhalte niemals unsynchronisiert sind und dass die Leistungseinbußen bei der Generierung von Mipmaps zur Laufzeit ausgeschlossen werden.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
- Konfigurieren des Quellbilds für die Verarbeitung mithilfe der Pipeline für Bildinhalte.  
  
- Konfigurieren der Pipeline für Bildinhalte zum Generieren von Mipmaps.  
  
## <a name="exporting-mipmaps"></a>Exportieren von Mipmaps  
 Mipmapping stellt im Bildschirmbereich automatisch die Detailebene für strukturierte Oberflächen in einem 3D-Spiel oder einer 3D-App bereit. Die Renderingleistung eines Spiels oder einer App wird mithilfe von vorberechneter komprimierter Versionen einer Textur erhöht, damit nicht jedes Mal die gesamte Textur komprimiert werden muss.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>So exportieren Sie eine Textur mit Mipmaps  
  
1. Beginnen Sie mit einer Standardtextur. Laden Sie eine vorhandene Datei, oder erstellen Sie eine, wie in [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md). Um Mipmaps zu unterstützen geben Sie eine Textur mit einer Breite und Höhe an, die beide in der Größe über die gleiche Potenz verfügen, z. B. 64x64, 256x256 oder 512x512.  
  
2. Konfigurieren Sie die soeben erstellte Texturdatei so, dass sie durch die Pipeline für Bildinhalte verarbeitet wird. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die soeben erstellte Texturdatei, und wählen Sie dann **Eigenschaften** aus. Legen Sie anschließend die Eigenschaft **Elementtyp** auf der Seite **Konfigurationseigenschaften**, **Allgemein** auf **Pipeline für Bildinhalte** fest. Stellen Sie sicher, dass die Eigenschaft **Inhalt** auf **JA** und die Option **Aus Build ausschließen** auf **NEIN** festgelegt ist. Wählen Sie dann die Schaltfläche **Übernehmen** aus. Die Eigenschaftenseite für die Konfiguration der **Pipeline für Bildinhalte** wird angezeigt.  
  
3. Konfigurieren Sie die Pipeline für Bildinhalte so, dass sie Mipmaps generiert. Legen Sie die Eigenschaft **MIPS generieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte**, **Allgemein** auf **JA (/generatemips)** fest.  
  
4. Klicken Sie auf die Schaltfläche **OK** .  
  
   Wenn Sie das Projekt erstellen, wird das Quellbild von der Pipeline für Bildinhalte vom Arbeitsformat in das angegebene Ausgabeformat konvertiert, einschließlich MIP-Ebenen. Das Ergebnis wird dann in das Ausgabeverzeichnis des Projekts kopiert.
