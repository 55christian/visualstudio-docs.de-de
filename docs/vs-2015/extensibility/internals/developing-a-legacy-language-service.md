---
title: Entwickeln eines Legacysprachdiensts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440118"
---
# <a name="developing-a-legacy-language-service"></a>Entwickeln eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Abschnitt enthält Links zu Themen, mit denen Sie erstellen einen legacy-Sprachdienst.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Modell eines Legacysprachdiensts](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Bietet ein Modell eines Diensts minimale Sprache für die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Kern-Editor. Sie können dieses Modell als Leitfaden verwenden, für das Erstellen eigener Sprachdiensts.  
  
 [Schnittstellen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Beschreibt die Objekte erforderlich, um einen Sprachdienst zu implementieren, und enthält eine Liste von zusätzlichen Objekten, die Sie verwenden können, um syntaxhervorhebung, Methodendaten und andere Funktionen bereitzustellen.  
  
 [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Beschreibt, wie zum Einfügen von eines Befehlsfilter in Ihren Sprachdienst, zum Abfangen von Befehlen, die andernfalls von die Textansicht behandelt würden.  
  
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Enthält Informationen zum Registrieren des Sprachdiensts mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Beschreibt, wie ein Sprachdienst Funktionen zur Unterstützung von eines Debuggers bereitstellen kann.  
  
 [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Enthält schrittweise Anleitungen zum Erstellen und die Integration von einem Sprachdienst für die Kern-Editor.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Erläutert, wie syntaxhervorhebung in den Sprachdienst zu implementieren.  
  
 [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Erläutert die Anweisungsvervollständigung, den Prozess mit dem ein Sprachdienst hilft Benutzern, die abgeschlossen wird, ein Programmiersprachen-Schlüsselwort oder das Element, die sie eingeben gestartet wurden.  
  
 [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Beschreibt, wie um methodentipps für überladene Funktionen und Methoden bereitzustellen.  
  
 [Vorgehensweise: Unterstützen von ausgeblendetem Text in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Erläutert den Zweck eines Bereichs von ausgeblendetem Text, und enthält Anweisungen dazu, wie Sie einen Bereich des ausgeblendeten Textes zu implementieren.  
  
 [Vorgehensweise: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Erläutert die zwei Optionen, die Gliederung für Ihre Sprache zu unterstützen, erweitert die *reduzieren auf Definitionen* Befehl.
