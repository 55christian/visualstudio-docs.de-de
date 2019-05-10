---
title: 'Vorgehensweise: Definieren des Typdeskriptors für einen Parameter | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18c2d5396b01c238213d494c1452e8919ea9cdd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971328"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Vorgehensweise: Definieren des Typdeskriptors für einen parameter
  Ein Typdeskriptor enthält Eigenschaften, mit denen der Datentyp eines Parameters beschrieben wird. Von einem Typdeskriptor kann ein Feld, eine Entität oder eine Auflistung von Entitäten definiert werden. Weitere Informationen finden Sie unter [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>So definieren Sie den Typdeskriptor für einen Parameter

1. In der **BDC-Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters.

2. Wählen Sie auf der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.

3. In der **Eigenschaften** legen die Eigenschaften des Typdeskriptors.

     In den folgenden Prozeduren wird beschrieben, wie ein Typdeskriptor als Feld, Entität oder Entitätsauflistung definiert wird.

### <a name="to-define-a-field"></a>So definieren Sie ein Feld

1. In der **Eigenschaften** legen die **Namen** Eigenschaft des Typdeskriptors auf den Namen eines Felds in den Typ, der die Entität darstellt (z. B.: **FirstName**).

2. In der Liste neben der **TypeName** -Eigenschaft, wählen Sie den entsprechenden Datentyp aufweisen (z. B. **Int32**).

     Weitere Informationen zu anderen optionalen Parametern finden Sie unter [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>So definieren Sie eine Entität

1. In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen Namen, der die Entität beschrieben (z. B.: **Wenden Sie sich an**).

2. Legen Sie die **TypeName** Eigenschaft, um den vollqualifizierten Namen des Typs, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.

    - Für eine Klasse in Ihrem Projekt, wählen Sie den Pfeil nach unten neben der **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte im Dialogfeld, das angezeigt wird, und wählen Sie dann die Klasse in Ihrem Projekt.

         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems. Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft zu einer Klasse in Ihrem Projekt.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.

         Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft auf einen Typ in einer Assembly, die Sie in der Projektmappe verweisen definiert.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name den Namespace und den Namen des Typs.

         Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft auf einen Typ im BDC-Objektmodell.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. In der **BDC-Methodendetails** , öffnen Sie die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **bearbeiten**.

     Die **BDC-Explorer** Fenster wird geöffnet.

4. In der **BDC-Explorer**, öffnen Sie das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen**.

     Dem Entitätstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Feld.

5. Wiederholen Sie Schritt 4, um für jedes Feld der Entität einen untergeordneten Typdeskriptor hinzuzufügen.

### <a name="to-define-a-collection-of-entities"></a>So definieren Sie eine Auflistung von Entitäten

1. In der **BDC-Methodendetails** Fenster, wählen Sie den Typdeskriptor des Parameters, den Sie möchten.

2. Wählen Sie auf der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.

3. In der **Eigenschaften** legen die **Namen** Eigenschaft, um einen Namen, der die Entität beschrieben (z. B.: **Kontaktiert**).

4. Legen Sie die **"IsCollection"** Eigenschaft **"true"**. Dadurch wird angegeben, dass es sich bei diesem Typdeskriptor um eine Auflistung von Entitäten handelt.

5. Legen Sie die **TypeName** Eigenschaft, um eine Zeichenfolge, enthält einen Verweis auf, die <xref:System.Collections.Generic.IEnumerable%601> Schnittstelle und der vollqualifizierte Name des Typs, der die Entität darstellt. Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.

   - Für eine Klasse in Ihrem Projekt, wählen Sie den Pfeil nach unten neben der **TypeName** -Eigenschaft, wählen Sie die **aktuelles Projekt** Registerkarte im Dialogfeld, das angezeigt wird, und wählen Sie dann die Klasse in Ihrem Projekt.

      Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB-Systems.

      Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft, um eine Auflistung von Klassen in Ihrem Projekt.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.BdcModel1.Contact, BdcModel1]`

   - Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.

      Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft, um eine Auflistung von Typen in einer Assembly, die Sie in der Projektmappe verweisen.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`

   - Bei Verwendung eines im BDC-Objektmodell definierten Typs enthält der vollqualifizierte Name lediglich den Namespace und den Namen des Typs.

      Im folgenden Beispiel wird den Wert des der **TypeName** Eigenschaft, um eine Auflistung von im BDC-Objektmodell definierten Typen.

      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`

6. In der **BDC-Methodendetails** , öffnen Sie die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie dann **bearbeiten**.

    Die **BDC-Explorer** Fenster wird geöffnet.

7. In der **BDC-Explorer**, öffnen Sie das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen**.

    Dem Auflistungstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt. Konfigurieren Sie diesen Typdeskriptor als Entität.

## <a name="see-also"></a>Siehe auch
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
