---
title: Nicht unterstützte Bearbeitungen in Visual Basic bearbeiten und fortfahren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076940"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Nicht unterstützte Bearbeitungen beim Bearbeiten und Fortsetzen in Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

"Bearbeiten und Fortfahren" bietet im Unterbrechungsmodus die Möglichkeit, die Programmausführung anzuhalten, Änderungen im Ausführungscode vorzunehmen und die Programmausführung mit den neu eingefügten Änderungen wieder aufzunehmen. Bearbeitungen von deklarativem Code, die die öffentliche Struktur einer Klasse beeinflussen, sind generell unzulässig. Viele der Bearbeitungen, die Sie ggf. an einer Methode, an Eigenschaftentext oder an privaten Deklarationen in einer Klasse vornehmen, sind dagegen zulässig.  
  
 Wenn Sie eine nicht unterstützte Änderungen vornehmen möchten, müssen Sie das Debuggen unterbrechen, die Änderungen vornehmen und eine neue Debugsitzung starten.  
  
### <a name="BKMK_MethodandPropertyBodyEdits"></a> Methode und Eigenschaftentext  
 **Nicht unterstützte Änderungen an statischen lokalen Variablen**: Hinzufügen oder Aktualisieren einer lokalen Variable oder eine statische lokale Variable entfernen, wenn das würde eines Kompilierungsfehler auf.  
  
 **Nicht unterstützte Änderungen an Generika**: Änderungen an der generischen Methode selbst oder am Text von generischen Methoden werden nicht unterstützt. Die Instanziierung eines generischen Typs oder Aufrufe von vorhandenen generischen Methoden können hinzugefügt, gelöscht oder geändert werden.  
  
 **Andere nicht unterstützten Änderungen**  
  
- Ändern der Aufrufanweisung für eine Methode in der Aufrufliste.  
  
- Hinzufügen eines `Try...Catch`-Blocks, wenn der Anweisungszeiger im `Catch`-Block oder im `Finally`-Block endet.  
  
- Entfernen einer `Try...Catch` Blocks, wenn der Anweisungszeiger sich in einer `Catch`Block oder der `Finally` Block.  
  
- Hinzufügen eines `Using`-Blocks um den aktuellen Anweisungszeiger herum.  
  
- Hinzufügen eines `SynchLock`-Blocks um den aktuellen Anweisungszeiger herum.  
  
### <a name="BKMK_AttributeEdits"></a> Bearbeitungen von Attributen  
 Von "Bearbeiten und Fortfahren" wird das Ändern von Attributen nicht unterstützt. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Definieren, Bearbeiten oder Löschen einer Attributklasse.  
  
- Hinzufügen eines Attributs.  
  
- Bearbeiten oder Entfernen eines vorhandenen Attributs.  
  
### <a name="BKMK_ClassDeclarationEdits"></a> Bearbeitungen von Klassendeklarationen  
 Die meisten Änderungen an Klassendeklarationen werden im Unterbrechungsmodus von "Bearbeiten und Fortfahren" nicht zugelassen. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Umbenennen, Löschen oder Ändern der Vererbung einer vorhandenen Klasse.  
  
- Implementieren einer neuen Schnittstelle oder Entfernen der Implementierung einer Schnittstelle.  
  
- Ändern von Modifizierern in einer Klasse.  
  
- Hinzufügen, Ändern oder Entfernen des `ComClass`-Status.  
  
- Bearbeiten der Deklaration einer generischen Klasse.  
  
### <a name="BKMK_ClassMemberDeclarationEdits"></a> Klassenmemberdeklarationen  
 Änderungen an Memberdeklarationen mit "Bearbeiten und Fortsetzen" sind in den meisten Fällen unzulässig. Beispielsweise können Sie weder die Signatur noch die Zugriffsebene eines Members ändern. Zudem können Sie Member nicht vollständig entfernen, wenn dies zu einem Kompilierungsfehler führen würde. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Shadowing einer vorhandenen Membervariablen durch Deklaration einer globalen Variablen oder einer Membervariablen mit demselben Namen im umschließenden Block.  
  
- Shadowing einer statischen lokalen Variablen durch Deklaration einer neuen Instanz innerhalb eines Blocks.  
  
- Entfernen von Ereignishandlern. Das Hinzufügen eines Ereignishandlers ist zulässig.  
  
- Definieren einer Eigenschaft oder Methode als Überladung, es sei denn, die Eigenschaft bzw. Methode ist `Private`, und der Name kommt in keiner aktiven Anweisung vor.  
  
- Hinzufügen oder Entfernen der `WithEvents`-Klausel einer Membervariablen.  
  
- Löschen eines Members.  
  
- Ändern einer Eigenschaft oder einer Methodendeklaration zum Beenden der Implementierung einer Schnittstelle.  
  
- Bearbeiten einer Methode, die Generics verwendet.  
  
- Ändern der Signatur oder des Rückgabetyps einer nicht privaten Eigenschaft oder Methode.  
  
- Überschreiben oder Shadowing des Members einer Basisklasse.  
  
- Hinzufügen eines neuen Felds in einer mit `SequentialLayout` oder `ExplicitLayout` markierten Klasse.  
  
- Ändern des `MustInherit`-Status bzw. `NotOverridable`-Status einer Methode.  
  
- Ändern der Zugriffsmodifizierer einer Eigenschaft oder einer Methode.  
  
- Ändern des Typs oder des Schreibschutzstatus eines Felds.  
  
- Ändern eines öffentlichen Felds.  
  
### <a name="BKMK_CompilerOptionEdits"></a> Bearbeitungen von Compileroptionen  
 Bei der Verwendung von "Bearbeiten und Fortfahren" im Unterbrechungsmodus ist es unzulässig, die folgenden Compileroptionen zu ändern, hinzuzufügen oder zu entfernen:  
  
- **Option Strict**  
  
- **Option Explicit**  
  
- **Option Compare**  
  
### <a name="BKMK_ConstantsEdits"></a> Bearbeitungen von Konstanten  
 Im Modus "Bearbeiten und Fortfahren" sind Änderungen an Konstanten nur sehr eingeschränkt möglich. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Hinzufügen oder Aktualisieren einer konstanten Variable.  
  
- Ändern des Typs oder des Werts einer Konstante.  
  
- Entfernen einer Konstante.  
  
### <a name="BKMK_DelegateandEventDeclarationEdits"></a> Bearbeitungen von Delegat- und Ereignis-Deklaration  
 Einige Änderungen von Delegaten und Ereignissen werden im Unterbrechungsmodus von „Bearbeiten und Fortfahren“ nicht zugelassen. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Ändern oder Löschen einer Delegatdefinition.  
  
- Löschen eines Ereignisses.  
  
### <a name="BKMK_EnumerationEdits"></a> Bearbeitungen von Enumerationen  
 Änderungen an Enumerationen (`Enums`) werden vom "Bearbeiten und Fortfahren im Unterbrechungsmodus nicht unterstützt. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Ändern des zugrunde liegenden Typs einer `Enum`.  
  
- Hinzufügen, Ändern oder Entfernen von Membern einer `Enum`.  
  
- Ändern des Zugriffsmodifizierers einer `Enum`.  
  
### <a name="BKMK_ExternalDeclarationsEdits"></a> Bearbeitungen externer Deklarationen  
 Im Allgemeinen können Sie die Deklarationen externer Methoden im Modus "Bearbeiten und Fortfahren" nicht ändern. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Hinzufügen oder Entfernen einer externen Deklaration.  
  
- Ändern der Signatur oder Marshallen von Attributen einer externen Deklaration.  
  
### <a name="BKMK_ImportsEdits"></a> Bearbeitungen von Importen  
 Mit "Bearbeiten und Fortfahren" können Sie im Unterbrechungsmodus keine `Imports`-Anweisungen hinzufügen, ändern oder entfernen.  
  
### <a name="BKMK_InterfaceDefinitionEdits"></a> Bearbeitungen von Schnittstellendefinitionen  
 Zwar dürfen Sie häufig Änderungen an Membern vornehmen, die Schnittstellen implementieren, allerdings sind im Modus "Bearbeiten und Fortfahren" im Allgemeinen keine Änderungen an den eigentlichen Schnittstellendefinitionen zulässig. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Hinzufügen, Ändern und Entfernen von Schnittstellenmembern.  
  
- Löschen einer vorhandenen Schnittstelle.  
  
- Ändern des Zugriffsmodifizierers einer Schnittstelle.  
  
- Ändern der Schnittstellenvererbungshierarchie.  
  
### <a name="BKMK_ModuleDeclarationEdits"></a> Von Moduldeklarationen  
 Die meisten Änderungen an Moduldeklarationen sind nicht zulässig, solange "Bearbeiten und Fortfahren" aktiviert ist und Sie sich im Unterbrechungsmodus befinden. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Erstellen eines neuen Moduls.  
  
- Umbenennen oder Löschen eines vorhandenen Moduls.  
  
- Ändern des Zugriffsmodifizierers für ein Modul.  
  
### <a name="BKMK_ModuleMemberDeclarationEdits"></a> Modulmemberdeklarationen  
 Mithilfe von "Bearbeiten und Fortfahren" können Sie im Unterbrechungsmodus eine Reihe von Änderungen an Modulmembern, z. B. Eigenschaften, Methoden und Feldern, vornehmen. Einige Änderungen werden jedoch nicht unterstützt. Von „Bearbeiten und Fortfahren“ wird vor allem das Hinzufügen, Löschen oder Ändern des Typs oder der Signatur eines Members nicht unterstützt.  
  
 Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Hinzufügen eines neuen Members, sofern keine Vorkommnisse mit dem Namen in einer aktiven Anweisung vorhanden sind.  
  
- Entfernen einer Eigenschaft oder Methode.  
  
- Ändern der Signatur einer Eigenschaft oder Methode.  
  
- Hinzufügen, Umbenennen, Verschieben oder Löschen eines Felds.  
  
- Bearbeiten einer Methode, die Generics verwendet.  
  
- Ändern der Zugriffsmodifizierer einer Eigenschaft oder Methode, z. B. `Public` in `Private`.  
  
- Löschen oder Ändern des Typs eines vorhandenen Felds.  
  
### <a name="BKMK_NestedTypeDeclarationEdits"></a> Deklarationsbearbeitungen des geschachtelten Typs  
 Durch „Bearbeiten und Fortfahren“ wird das Verschieben eines geschachtelten Typs zu einem anderen Namespace oder Typ nicht unterstützt.  
  
### <a name="BKMK_StructureDeclarationEdits"></a> Bearbeitungen von Strukturdeklarationen  
 Die meisten Änderungen an Strukturdeklarationen sind nicht zulässig, bearbeiten und fortfahren, während in **unterbrechen** Modus. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Umbenennen bzw. Löschen einer vorhandenen Struktur.  
  
- Implementieren einer neuen Schnittstelle oder Entfernen der Implementierung einer Schnittstelle.  
  
- Ändern des Zugriffsmodifizierers für eine Struktur.  
  
### <a name="BKMK_StructureMemberDeclarationEdits"></a> Strukturmemberdeklarationen  
 Mithilfe von "Bearbeiten und Fortfahren" können Sie im Unterbrechungsmodus eine Reihe von Änderungen an Strukturmembern (Eigenschaften, Methoden und Feldern) vornehmen. Einige Änderungen werden jedoch nicht unterstützt, insbesondere Änderungen, die die Deklaration von Strukturmembern beeinflussen. Insbesondere werden von "Bearbeiten und Fortfahren" die folgenden Änderungen nicht unterstützt:  
  
- Entfernen einer Eigenschaft oder Methode.  
  
- Hinzufügen oder Entfernen eines Felds.  
  
- Ändern der Signatur einer Eigenschaft oder Methode.  
  
- Bearbeiten einer Methode, die Generics verwendet.  
  
- Ändern, ob eine Eigenschaften- oder Methodendeklaration eine Schnittstelle implementiert oder nicht.  
  
- Ändern der Zugriffsmodifizierer einer Eigenschaft oder Methode (z. B. `Public` zu **Private**).  
  
- Entfernen eines Felds.  
  
- Ändern des Typs eines Felds.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
