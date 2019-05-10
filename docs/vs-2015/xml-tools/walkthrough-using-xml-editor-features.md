---
title: 'Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55e7cdc06b1876fe40310f5af44152a70e4a4375
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438883"
---
# <a name="walkthrough-using-xml-editor-features"></a>Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML-Dokuments. Bei der exemplarischen Vorgehensweise werden auch die Funktionen des XML-Editors verwendet, die für das Verfassen von XML nützlich sind.  
  
> [!NOTE]
> Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei hireDate.xsd (weiter unten in diesem Thema aufgeführt) auf dem lokalen Computer.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen ihr ein XML-Schema zu  
  
1. Auf der **Datei** Startmenü **neu**, und klicken Sie auf **Datei**.  
  
2. Wählen Sie **XML-Datei** in die **Vorlagen** Bereich, und klicken Sie auf **öffnen**.  
  
     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.  
  
3. Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Schemas** Feld.  
  
     Die **XSD-Schemas** Dialogfeld wird angezeigt.  
  
4. Klicken Sie auf **Hinzufügen**.  
  
     Die **XSD-Schema öffnen** Dialogfeld wird angezeigt.  
  
5. Wählen Sie die hireDate.xsd-Datei, und klicken Sie auf **öffnen**.  
  
6. Klicken Sie auf **OK**.  
  
     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet. Mithilfe des XML-Schemas wird das Dokument validiert. Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.  
  
### <a name="to-add-data"></a>So fügen Sie Daten hinzu  
  
1. Geben Sie im Editorbereich `<` ein.  
  
     In der Memberliste werden die möglichen Elemente angezeigt:  
  
    - **!--** zum Hinzufügen eines Kommentars.  
  
    - **! DOCTYPE** zum Hinzufügen eines Dokumenttyps.  
  
    - **?** zum Hinzufügen einer Verarbeitungsanweisung.  
  
    - **Mitarbeiter** zum Hinzufügen eines Stammelements.  
  
2. Wählen Sie  **\<!--** einen Kommentarknoten hinzuzufügen, und drücken EINGABETASTE.  
  
     Der Editor fügt ein Kommentar-Endtag ein und platziert den Cursor zwischen dem Start- und Endtag des Kommentars.  
  
3. Geben Sie in **XML-Testdatei**.  
  
4. Geben Sie auf einer neuen Zeile `<`, und wählen Sie **Mitarbeiter** in der Memberliste aus.  
  
     Im Editor wird der Anfang eines XML-Elements, `<employee`, hinzugefügt. An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.  
  
5. Geben Sie `>` ein, um das Tag zu schließen.  
  
6. Der Editor fügt das Endtag hinzu. Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird. Die QuickInfo wird die Meldung angezeigt: Das Element "Employee" ist Inhalt unvollständig. Erwartet wurde 'ID'.  
  
7. Typ `<` , und wählen Sie **ID** in der Memberliste aus. Geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID-Starttag.  
  
8. Typ **Abc**.  
  
     Die **Abc** Text weist eine wellenförmige Unterstreichung. Die QuickInfo wird die Meldung angezeigt: Das Element "ID" hat einen ungültigen Wert gemäß seinem Datentyp.  
  
9. Klicken Sie mit der rechten Maustaste auf das ID-Element, und wählen Sie **Gehe zu Definition**.  
  
     Der Editor öffnet die Datei hireDate.xsd in einem neuen Dokumentfenster und platziert den Cursor auf der ID-Schemaelementdefinition.  
  
10. Zurückgeben der XML-Datei, und Ersetzen Sie die **Abc** Text mit **123**.  
  
     Die wellenförmige Unterstreichung und die Quickinfo unter dem ID-Elementwert werden gelöscht. Die QuickInfo für das Endtag des Mitarbeiters wird jetzt die Meldung angezeigt: Das Element "Employee" ist Inhalt unvollständig. Erwartet wurde 'hire-date'.  
  
11. Positionieren Sie den Cursor hinter dem ID-Endtag, geben Sie `<` ein, wählen Sie „hire-date“ in der Memberliste aus, und geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire-date'-Starttag.  
  
12. Geben Sie in **2003-01-10** für den ' Hire-Date-Wert.  
  
### <a name="to-format-the-xml-document"></a>So formatieren Sie das XML-Dokument  
  
1. Wählen Sie die **Dokument formatieren** der XML-Editor-Symbolleiste die Schaltfläche.  
  
     Das XML-Dokument wird neu formatiert.  
  
### <a name="to-save-the-xml-document"></a>So speichern Sie das XML-Dokument  
  
1. Von der **Datei** , wählen Sie im Menü **speichern**.  
  
     Die **Datei speichern unter** Dialogfeld wird angezeigt. Der Standarddateiname lautet 'XMLFile1'.  
  
2. Geben Sie den Dateinamen und Speicherort für das XML-Dokument aus, und klicken Sie auf **speichern**.  
  
## <a name="hiredatexsd-file"></a>Die Datei "hireDate.xsd"  
 Bei der exemplarischen Vorgehensweise wird die folgende Schemadatei verwendet.  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)
