---
title: 'Gewusst wie: Erstellen von XML-Ausschnitten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e08821f1289927c4183a1639ae37136c220a88c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670904"
---
# <a name="how-to-create-xml-snippets"></a>Vorgehensweise: Erstellen von XML-Ausschnitten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe des XML-Editors können neue XML-Ausschnitte erstellt werden. Der Editor enthält einen XML-Ausschnitt mit dem Namen "Snippet". Dies ist ein vorformulierter Ausschnitt zum Erstellen neuer XML-Ausschnitte.

## <a name="to-create-a-new-xml-snippet"></a>So erstellen Sie einen neuen XML-Ausschnitt
 Um einen neuen XML-Code Ausschnitt zu erstellen, erstellen Sie eine neue XML-Datei, und verwenden Sie das Feature " **Ausschnitt einfügen** ".

1. Klicken Sie im Menü **Datei** auf **neu** , und klicken Sie dann auf **Datei**.

2. Klicken Sie auf **XML-Datei** und dann auf **Öffnen**.

3. Klicken Sie mit der rechten Maustaste in den Bereich Editor, und wählen Sie **Ausschnitt einfügen**aus.

4. Wählen Sie in der Liste **Ausschnitt** aus, und drücken Sie die EINGABETASTE.

5. Nehmen Sie die gewünschten Änderungen an dem neuen Ausschnitt vor.

6. Wählen Sie im Menü **Datei** die Option **xmlfile. XML speichern**aus.

     Das Dialogfeld **Datei speichern** unter wird angezeigt.

7. Geben Sie den Namen für den neuen Code Ausschnitt ein, und wählen Sie im Dropdown Fenster **Dateityp** die Option **Ausschnitt Dateien** aus.

8. Verwenden Sie die Dropdown Liste **Speichern in** , um den Datei Speicherort in den Ordner My Documents\Visual Studio 2005 \ Code snippeer \ xml\my XML Snippets zu ändern, und klicken Sie dann auf **Save**.

## <a name="snippet-description"></a>Ausschnittbeschreibung
 In diesem Abschnitt werden einige Schlüsselelemente im vorformulierten Ausschnitt beschrieben. Weitere Informationen zu Schema Elementen, die von den XML-Ausschnitten verwendet werden, finden Sie unter [Schema Referenz für Code Ausschnitte](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType-Element
 Vom Editor werden zwei Ausschnitttypen unterstützt:

```
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 Der `Expansion` Typ bestimmt, ob der Ausschnitt angezeigt wird, wenn Sie den Befehl **Ausschnitt einfügen** aufrufen. Der `SurroundsWith`-Typ bestimmt, ob der Ausschnitt angezeigt wird, wenn Sie den Befehl "umschließen **mit** " aufrufen.

### <a name="code-element"></a>Codeelement
 Das `Code`-Element definiert den XML-Text, der beim Aufrufen des Ausschnitts eingefügt wird.

> [!NOTE]
> Der XML-Ausschnitttext muss in einem `<![CDATA[...]]>`-Abschnitt eingeschlossen werden.

 Es folgt das `Code`-Element, das von einem vorformulierten Ausschnitt erstellt wurde.

```
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 Das `Code`-Element enthält drei Variablen.

- $name$ ist eine benutzerdefinierte Variable. Sie erstellt ein `name`-Element mit einem editierbaren Wert, dessen Standardwert "name" ist. Benutzerdefinierte Variablen werden mithilfe des `Literal`-Elements definiert.

- $selected$ ist eine vordefinierte Variable. Sie stellt den Text dar, der im XML-Editor vor dem Aufrufen des Ausschnitts ausgewählt wurde. Die Positionierung dieser Variablen bestimmt, an welcher Position der ausgewählte Text im Codeausschnitt angezeigt wird, der die Auswahl umgibt.

- $end$ ist eine vordefinierte Variable. Wenn der Benutzer die EINGABETASTE drückt, um die Bearbeitung der Codeausschnittfelder zu beenden, bestimmt diese Variable, an welche Position das Caretzeichen (^) verschoben wird.

  Das obige `Code`-Element fügt den folgenden XML-Text ein:

```
<test>
  <name>name</name>
</test>
```

 Der Wert des name-Elements wird als editierbarer Bereich gekennzeichnet.

### <a name="literal-element"></a>Literalelement
 Mithilfe des `Literal`-Elements wird der Ersetzungstext angegeben, der nach dem Einfügen in die Datei angepasst werden kann. Literalzeichenfolgen, numerische Werte und einige Variablennamen können beispielsweise als Literale deklariert werden. Sie können in einem XML-Ausschnitt beliebig viele Literale definieren, und Sie können darauf mehrfach aus dem Ausschnitt verweisen. Es folgt ein Beispiel für ein `Literal`-Element, das eine $name$-Variable definiert, deren Standardwert "name" ist.

```
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 Literale können auch auf Funktionen verweisen. Der XML-Editor enthält eine Funktion mit dem Namen **LookupPrefix**. Die **LookupPrefix** -Funktion sucht den angegebenen Namespace-URI von dem Speicherort im XML-Dokument, von dem aus dieser Ausschnitt aufgerufen wird, und gibt das Namespace Präfix zurück, das für diesen Namespace definiert ist, sofern vorhanden, und enthält den Doppelpunkt (:) in diesem Namen. Im folgenden finden Sie ein Beispiel für ein `Literal`-Element, das die **LookupPrefix** -Funktion verwendet.

```
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 Die $prefix$-Variable kann anschließend an beliebiger Stelle im XML-Ausschnitt verwendet werden.

## <a name="see-also"></a>Siehe auch
 [XML-Ausschnitte](../xml-tools/xml-snippets.md) Gewusst [wie: Verwenden von XML](../xml-tools/how-to-use-xml-snippets.md) -Ausschnitten Gewusst [wie: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
