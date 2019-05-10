---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064725"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPackage-Projektvorlage kann einen einfachen, benutzerdefinierten Editor in C++ erstellen.  Die VSPackage-Projektvorlage wird C#- oder Visual Basic-Projekte nicht mehr unterstützt. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Die Visual Studio-Paket-Projektvorlage  
 Die Visual Studio-Paket-Projektvorlage finden Sie in der **neues Projekt** Dialogfeld im Ordner "C++-Erweiterungen"  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen Sie eine VSPackage mithilfe der Visual Studio-Paket-Vorlage  
  
1. Erstellen Sie ein Projekt mit der Visual Studio-Paket-Vorlage.  
  
2. Wählen Sie die **Editor für benutzerdefinierte** aus, und klicken Sie auf **Weiter**. Die **Editoroptionen** angezeigt wird.  
  
3. Geben Sie den Namen des Editors in die **editorname** Feld. Geben Sie die Dateierweiterung, die Ihr Editor im zugeordnet werden sollen die **Dateierweiterung** Feld. Ihre-Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Dateierweiterung ist nicht für Windows nur für Visual Studio registriert. Geben Sie der Standarddateiname für neue Dokumente erstellt, die mit Ihrem-Editor in die **Standarddateiname** Feld.  
  
4. Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.  
  
### <a name="to-test-your-custom-editor"></a>Zum Testen des benutzerdefinierten Editors  
  
1. Auf der **Datei** Startmenü **neu** , und klicken Sie dann auf **Datei**.  
  
2. In der **installierte Vorlagen** im Bereich der **neue Datei** wählen Sie im Dialogfeld die Dateivorlage, und klicken Sie dann auf die Datei, Sie gerade registriert geben.  
  
3. Klicken Sie auf **öffnen** anzeigen und bearbeiten das Dokument.  
  
     Der Editor unterstützt Ausschneiden und einfügen, suchen und ersetzen und Open-and-Load-Vorgänge.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)
