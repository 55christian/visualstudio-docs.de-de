---
title: 'Exemplarische Vorgehensweise: Erstellen einen WCF-Datendienst mit WPF und Entitätsframework | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12d7e9c25cdf4e0431a7e4b5e3639dc59b76790c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703176"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Exemplarische Vorgehensweise: Erstellen eines WCF-Datendiensts mit WPF und Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Erstellen eines einfachen [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , befindet sich einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Webanwendung, und klicken Sie dann eine Windows Forms-Anwendung zugreifen.  
  
 In dieser exemplarischen Vorgehensweise werden Sie:  
  
- Eine Webanwendung erstellen, um einen [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] zu hosten.  
  
- Ein [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] zur Darstellung der Tabelle "Customers" in der Northwind-Datenbank erstellen.  
  
- Erstellen Sie eine [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
- Eine Clientanwendung erstellen und dieser einen Verweis auf den [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] hinzufügen.  
  
- Die Datenbindung zum Dienst aktivieren und die Benutzeroberfläche erstellen.  
  
- Optional Filterfunktionen zur Anwendung hinzufügen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
- Die Beispieldatenbank Northwind.  
  
     Befindet sich diese Datenbank nicht auf Ihrem Entwicklungscomputer, können Sie sie aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088)herunterladen. Anweisungen hierzu finden Sie unter [Herunterladen von Beispieldatenbanken](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Erstellen des Diensts  
 Um einen [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] zu erstellen, fügen Sie ein Webprojekt hinzu. Dann erstellen Sie ein [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] und erstellen anschließend den Dienst aus dem Modell.  
  
 Im ersten Schritt fügen Sie ein Webprojekt zum Hosten des Diensts hinzu.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>So erstellen Sie das Webprojekt  
  
1. Wählen Sie auf der Menüleiste **Datei**, **neu**, **Projekt**.  
  
2. Erweitern Sie im Dialogfeld **Neues Projekt** die Knoten **Visual Basic** oder **Visual C#** sowie **Web**, und wählen Sie dann die Vorlage **ASP.NET-Webanwendung** aus.  
  
3. Geben Sie **NorthwindWeb** im Textfeld **Name** ein, und wählen Sie dann die Schaltfläche **OK**.  
  
4. Wählen Sie im Dialogfeld **Neues ASP.NET-Projekt** aus der Liste **Vorlage auswählen** die Option **Leer**, und klicken Sie dann auf die Schaltfläche **OK**.  
  
   In diesem Schritt erstellen Sie ein [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] zur Darstellung der Tabelle "Customers" in der Northwind-Datenbank.  
  
#### <a name="to-create-the-entity-data-model"></a>So erstellen Sie das Entity Data Model  
  
1. Wählen Sie auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Daten** und anschließend das Element **ADO.NET Entity Data Model** aus.  
  
3. In der **Namen** Text geben `NorthwindModel`, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
    Der Assistent für Entity Data Model wird angezeigt.  
  
4. Wählen Sie im Entity Data Model-Assistenten auf der Seite **Modellinhalte auswählen** das Element **EF-Designer aus Datenbank** aus, und klicken Sie dann auf **Weiter**.  
  
5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:  
  
   - Wenn eine Datenverbindung mit der Beispieldatenbank Northwind in der Dropdownliste verfügbar ist, wählen Sie sie aus.  
  
        - oder -   
  
   - Wählen Sie die Schaltfläche **Neue Verbindung**, um eine neue Datenverbindung zu konfigurieren. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
6. Wenn für die Datenbank ein Kennwort erforderlich ist, klicken Sie auf das Optionsfeld **Ja, vertrauliche Daten in die Verbindungszeichenfolge einschließen** und dann auf die Schaltfläche **Weiter**.  
  
   > [!NOTE]
   > Wenn ein Dialogfeld angezeigt wird, klicken Sie auf **Ja**, um die Datei im Projekt zu speichern.  
  
7. Wählen Sie auf der Seite **Wählen Sie Ihre Version** das Optionsfeld **Entity Framework 5.0** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.  
  
   > [!NOTE]
   > Um die aktuelle Version vom Entity Framework 6 mit WCF-Diensten zu verwenden, müssen Sie das WCF Data Services Entity Framework Provider NuGet-Paket installieren. Finden Sie unter [Verwenden von WCF Data Services 5.6.0 mit Entitätsframework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, aktivieren Sie das Kontrollkästchen **Customers**, und wählen Sie dann die Schaltfläche **Fertig stellen**.  
  
    Das Entitätsmodelldiagramm wird angezeigt, und dem Projekt wird die Datei NorthwindModel.edmx hinzugefügt.  
  
   In diesem Schritt erstellen und testen Sie den Datendienst.  
  
#### <a name="to-create-the-data-service"></a>So erstellen Sie den Datendienst  
  
1. Wählen Sie auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Web** und anschließend das Element **WCF Data Service 5.6**.  
  
3. In der **Namen** Text geben `NorthwindCustomers`, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
    Die Datei "NorthwindCustomers.svc" wird angezeigt, der **Code-Editor**.  
  
4. Suchen Sie im **Code-Editor`TODO:` den ersten** -Kommentar, und ersetzen Sie den Code durch Folgendes:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Ersetzen Sie die Kommentare im `InitializeService`-Ereignishandler durch folgenden Code:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. Wählen Sie auf der Menüleiste **Debuggen**, **Starten ohne Debugging** zum Ausführen des Diensts. Ein Browserfenster wird geöffnet, und das XML-Schema für den Dienst wird angezeigt.  
  
7. In der **Adresse** geben `Customers` am Ende der URL für die NorthwindCustomers.svc, und wählen Sie dann die **EINGABETASTE** Schlüssel.  
  
    Eine XML-Darstellung der Daten in der Tabelle "Customers" wird angezeigt.  
  
   > [!NOTE]
   > In einigen Fällen interpretiert Internet Explorer die Daten fälschlicherweise als RSS-Feed. Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist. Weitere Informationen finden Sie unter [Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md).  
  
8. Schließen Sie das Browserfenster.  
  
   In den nächsten Schritten erstellen Sie eine Windows Forms-Clientanwendung zur Verwendung des Diensts.  
  
## <a name="creating-the-client-application"></a>Erstellen der Clientanwendung  
 Zum Erstellen der Clientanwendung fügen Sie ein zweites Projekt hinzu, dem Sie einen Dienstverweis hinzufügen. Daraufhin konfigurieren Sie eine Datenquelle, und erstellen eine Benutzeroberfläche zum Anzeigen der Daten des Diensts.  
  
 Im ersten Schritt fügen Sie der Projektmappe ein Windows Forms-Projekt hinzu und legen dieses als Startprojekt fest.  
  
#### <a name="to-create-the-client-application"></a>So erstellen Sie die Clientanwendung  
  
1. Wählen Sie auf der Menüleiste Datei **hinzufügen**, **neues Projekt**.  
  
2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten, und wählen Sie die **Windows** Knoten, und wählen Sie dann auf  **Windows Forms-Anwendung**.  
  
3. Geben Sie im Textfeld **Name** `NorthwindClient` ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
4. Wählen Sie im **Projektmappen-Explorer** den **NorthwindClient**-Projektknoten.  
  
5. Wählen Sie in der Menüleiste **Projekt**, **Als Startprojekt festlegen** aus.  
  
   In diesem Schritt fügen Sie dem [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] im Webprojekt einen Dienstverweis hinzu.  
  
#### <a name="to-add-a-service-reference"></a>So fügen Sie einen Dienstverweis hinzu  
  
1. Wählen Sie auf der Menüleiste **Projekt**, **Hinzufügen eines Dienstverweises**.  
  
2. Wählen Sie im Dialogfeld **Dienstverweis hinzufügen** die Schaltfläche **Ermitteln** aus.  
  
    Die URL für den NorthwindCustomers-Dienst wird im Feld **Adresse** angezeigt.  
  
3. Klicken Sie auf die Schaltfläche **OK**, um den Dienstverweis hinzuzufügen.  
  
   In diesem Schritt konfigurieren Sie eine Datenquelle, um die Datenbindung zum Dienst zu aktivieren.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>So aktivieren Sie die Datenbindung zum Dienst  
  
1. Wählen Sie auf der Menüleiste **Ansicht**, **Other Windows**, **Datenquellen**.  
  
2. Wählen Sie im Fenster **Datenquellen** die Schaltfläche **Neue Datenquelle hinzufügen**.  
  
3. Wählen Sie auf der Seite **Datenquellentyp auswählen** unter **Assistent zum Konfigurieren von Datenquellen** den Typ **Objekt** und dann die Schaltfläche **Weiter**.  
  
4. Erweitern Sie auf der Seite **Datenobjekte auswählen** den Knoten **NorthwindClient**, und erweitern Sie dann den Knoten **NorthwindClient.ServiceReference1**.  
  
5. Aktivieren Sie das Kontrollkästchen **Customer**, und wählen Sie dann **Fertig stellen**.  
  
   In diesem Schritt erstellen Sie die Benutzeroberfläche, auf der die Daten des Diensts angezeigt werden.  
  
#### <a name="to-create-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche  
  
1. Im Fenster **Datenquellen** öffnen Sie das Kontextmenü für den Knoten **Customers** und wählen **Kopieren** aus.  
  
2. Öffnen Sie im Formular-Designer **Form1.vb** oder **Form1.cs** das Kontextmenü, und wählen Sie **Einfügen** aus.  
  
    Ein <xref:System.Windows.Forms.DataGridView>-Steuerelement, eine <xref:System.Windows.Forms.BindingSource>-Komponente und eine <xref:System.Windows.Forms.BindingNavigator>-Komponente werden dem Formular hinzugefügt.  
  
3. Wählen Sie das **CustomersDataGridView**-Steuerelement aus, und legen Sie dann im Fenster **Eigenschaften** die Eigenschaft **Andocken** auf **Füllbereich** fest.  
  
4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Form1** Knoten, und wählen Sie **Anzeigecode** , öffnen Sie den Code-Editor, und fügen die folgende Imports- oder Using-Anweisung in der Anfang der Datei:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:  
  
   ```vb  
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
           Dim proxy As New NorthwindEntities _  
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
           Me.CustomersBindingSource.DataSource = proxy.Customers  
       End Sub  
   ```  
  
   ```csharp  
   private void Form1_Load(object sender, EventArgs e)  
   {  
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
   this.CustomersBindingSource.DataSource = proxy.Customers;  
   }  
  
   ```  
  
6. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die NorthwindCustomers.svc-Datei, und wählen Sie **in Browser anzeigen**. Das XML-Schema für den Dienst wird im Internet Explorer angezeigt.  
  
7. Kopieren Sie die URL aus der Adressleiste von Internet Explorer.  
  
8. Markieren Sie in dem in Schritt 4 hinzugefügten Code den Text `http://localhost:53161/NorthwindCustomers.svc/`, und ersetzen Sie diesen durch die soeben kopierte URL.  
  
9. Wählen Sie auf der Menüleiste **Debuggen**, **Debuggen starten** zum Ausführen der Anwendung. Die Kundeninformationen werden angezeigt.  
  
   Sie verfügen nun über eine funktionierende Anwendung, die eine Liste der Kunden aus dem NorthwindCustomers-Dienst anzeigt. Wenn Sie weitere Daten über den Dienst bereitstellen möchten, können Sie das [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] so bearbeiten, dass zusätzliche Tabellen aus der Northwind-Datenbank eingebunden werden.  
  
   Im nächsten optionalen Schritt erfahren Sie, wie die vom Dienst zurückgegebenen Daten gefiltert werden.  
  
## <a name="adding-filtering-capabilities"></a>Hinzufügen von Filterfunktionen  
 In diesem Schritt passen Sie die Anwendung an, um die Daten nach dem Wohnort des Kunden zu filtern.  
  
#### <a name="to-add-filtering-by-city"></a>So fügen Sie Filterung anhand des Wohnorts hinzu  
  
1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für den Knoten **Form1.vb** oder **Form1.cs**, und wählen Sie dann **Öffnen** aus.  
  
2. Fügen Sie dem Formular ein <xref:System.Windows.Forms.TextBox>- und ein <xref:System.Windows.Forms.Button>-Steuerelement aus der **Toolbox** hinzu.  
  
3. Öffnen Sie das Kontextmenü für die <xref:System.Windows.Forms.Button> steuern, und wählen Sie **Anzeigecode**, und fügen Sie den folgenden Code in die `Button1_Click` -Ereignishandler:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4. Ersetzen Sie im vorherigen Code den Text `http://localhost:53161/NorthwindCustomers.svc` durch die URL aus dem `Form1_Load`-Ereignishandler.  
  
5. Wählen Sie auf der Menüleiste **Debuggen**, **Debuggen starten** zum Ausführen der Anwendung.  
  
6. Geben Sie im Textfeld die Zeichenfolge **London** ein, und klicken Sie dann auf die Schaltfläche. Nur die Kunden aus London werden angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Vorgehensweise: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
