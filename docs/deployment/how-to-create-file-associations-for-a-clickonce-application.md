---
title: 'Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15d9b81bd342ccd8a5ee3377323e140ab1167c10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899459"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Vorgehensweise: Erstellen von Dateizuordnungen für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können eine oder mehrere Dateierweiterungen zugeordnet sein, damit die Anwendung automatisch gestartet wird, wenn der Benutzer eine Datei mit diesen Typen wird geöffnet. Hinzufügen von Unterstützung für Dateinamen-Erweiterung auf einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist einfach.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Zum Erstellen von dateizuordnungen für eine ClickOnce-Anwendung

1. Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung normal, oder verwenden Sie die vorhandene [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

2. Öffnen Sie das Anwendungsmanifest mit einem Text- oder XML-Editor wie Editor.

3. Suchen Sie das `assembly` -Element. Weitere Informationen finden Sie unter [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).

4. Als untergeordnetes Element der `assembly` -Element, Hinzufügen einer `fileAssociation` Element. Die `fileAssociation` Element verfügt über vier Attribute:

   - `extension`: Die Dateinamenerweiterung, die Sie der Anwendung zuordnen möchten.

   - `description`: Eine Beschreibung des Dateityps, die in der Windows-Shell angezeigt wird.

   - `progid`: Eine Zeichenfolge, die den Dateityp aus, um es in der Registrierung markieren eindeutig identifiziert.

   - `defaultIcon`: Ein Symbol für diesen Dateityp verwendet werden soll. Das Symbol muss als eine Ressource im Manifest Anwendung hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Ein Beispiel für die `file` und `fileAssociation` Elemente finden Sie unter [ \<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md).

5. Wenn Sie die Anwendung mehr als einen Dateityp zuordnen möchten, fügen Sie zusätzliche `fileAssociation` Elemente. Beachten Sie, dass die `progid` Attribut sollte unterschiedlich sein.

6. Sobald Sie mit dem Anwendungsmanifest abgeschlossen haben, Signieren Sie das Manifest erneut. Sie erreichen dies über die Befehlszeile mit *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Weitere Informationen finden Sie unter [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Siehe auch
- [\<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)