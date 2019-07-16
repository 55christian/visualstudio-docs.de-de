---
title: Kommentieren von Code in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160905"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Kommentieren von Code in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Programmiersprachen bieten in der Regel eine Möglichkeit zum Kommentieren oder kommentieren Sie den Code. Ein Kommentar ist einen Textabschnitt, der enthält zusätzliche Informationen zu den Code wird jedoch ignoriert, während der Kompilierung oder Interpretation erfordern.  
  
 Die verwaltete Package Framework (MPF)-Klassen bieten Unterstützung für auskommentieren und Aufheben der auskommentierung markierten Text.  
  
## <a name="comment-styles"></a>Kommentarstile  
 Es gibt zwei allgemeine Arten der Kommentar:  
  
1. Zeilenkommentare, die der Kommentar, in dem in einer einzelnen Zeile ist.  
  
2. Block-Kommentare, in dem der Kommentar auf mehrere Zeilen enthalten kann.  
  
   Zeilenkommentare haben in der Regel ein (oder die Anfangszeichen), während blockskommentaren sowohl Start-und Endzeichen haben. In c# ein Zeilenkommentar starten z. B. mit / /, und ein blockskommentar beginnt mit / * und endet mit \*/.  
  
   Wenn der Benutzer den Befehl auswählt **Auswahl kommentieren** aus der **bearbeiten** -> **erweitert** im Menü der Befehl geleitet wird die <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse. Wenn der Benutzer den Befehl auswählt **Kommentar der Auswahl**, der Befehl weitergeleitet wird, um die <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> Methode.  
  
## <a name="supporting-code-comments"></a>Unterstützung von Kommentaren im Code  
 Sie haben Ihre Language Service Support Codekommentare von der `EnableCommenting` benannter Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Hiermit wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Weitere Informationen zum Festlegen der Sprache Servicce-Features finden Sie unter [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> -Methode zur Rückgabe einer <xref:Microsoft.VisualStudio.Package.CommentInfo> Struktur mit die Kommentarzeichen für Ihre Sprache. C#-Stil zeilenkommentarzeichen sind die Standardeinstellungen.  
  
### <a name="example"></a>Beispiel  
 Hier ist eine Beispiel einer Implementierung der <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Methode.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
