---
title: "Proc&#233;dure pas &#224; pas&#160;: ajout d&#39;une page d&#39;application &#224; un flux de travail | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "page d'application (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, ajouter une page d'application à un workflow"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Proc&#233;dure pas &#224; pas&#160;: ajout d&#39;une page d&#39;application &#224; un flux de travail
  Cette procédure pas à pas explique comment ajouter une page d'application présentant les données dérivées d'un flux de travail dans un projet de flux de travail.  Elle repose sur le projet décrit à la rubrique [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Ajout d'une page d'application ASPX à un projet de flux de travail SharePoint.  
  
-   Extraction et manipulation des données du projet de flux de travail.  
  
-   Présentation des données sous forme de tableau dans la page d'application.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Vous devez également terminer le projet dont il est question à la rubrique [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## Modification du code de flux de travail  
 Commencez par ajouter une ligne de code au flux de travail afin d'affecter à la colonne Résultat une valeur correspondant au montant de la note de frais.  Cette valeur sera utilisée ultérieurement lors du calcul de la note de frais.  
  
#### Pour définir la valeur de la colonne Résultat dans le flux de travail  
  
1.  Chargez le projet réalisé à la rubrique [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Ouvrez le code de Workflow1.cs ou Workflow1.vb \(selon votre langage de programmation\).  
  
3.  Insérez le code suivant en bas de la méthode `createTask1_MethodInvoking` :  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## Création d'une page d'application  
 Veuillez ensuite ajouter un formulaire ASPX au projet.  Ce formulaire a pour fonction d'afficher les données obtenues à partir du projet de flux de travail de note de frais.  Pour ce faire, il convient de prévoir une page d'application.  Ce type de page utilise la même page maître que les autres pages SharePoint et présente donc très peu de différences par rapport aux autres pages sur le site SharePoint.  
  
#### Pour ajouter une page d'application au projet  
  
1.  Sélectionnez le projet ExpenseReport, puis, dans la barre de menus, sélectionnez **Projet**, **Ajouter un nouvel élément**.  
  
2.  Dans le volet de **Modèles**, sélectionnez le modèle **Page d'application**, utilisez le nom par défaut de l'élément de projet \(**ApplicaitonPage1.aspx**\), puis choisissez le bouton **Ajouter**.  
  
3.  Dans le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] du fichier ApplicationPage1.aspx, remplacez la section `PlaceHolderMain` par la section suivante :  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Ce code a pour effet d'ajouter une table à la page avec un titre.  
  
4.  Ajoutez un titre à la page d'application en remplaçant la section `PlaceHolderPageTitleInTitleArea` par la section suivante :  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## Codage de la page d'application  
 Ajoutez, à présent, le code nécessaire à la page d'application du résumé de la note de frais.  Lorsque vous ouvrirez la page, le code recherchera, dans la liste des tâches du site SharePoint, les dépenses ayant dépassé la limite fixée.  Le rapport contiendra un récapitulatif de chaque élément avec le montant des dépenses y afférant.  
  
#### Pour coder la page d'application  
  
1.  Cliquez sur le noeud **ApplicationPage1.aspx**, puis, dans la barre de menu, cliquez sur **Affichage**, **Code** pour afficher le code correspondant à la page d'application.  
  
2.  Remplacez les instructions **using** ou **Import** \(selon votre langage de programmation\) en haut de la classe par ce qui suit :  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  Ajoutez le code suivant à la méthode `Page_Load` :  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  Veillez à remplacer « TestServer » dans le code par le nom d'un serveur valide qui exécute SharePoint.  
  
## Test de la page d'application  
 Vérifiez ensuite si la page d'application affiche correctement les données de la note de frais.  
  
#### Pour tester la page d'application  
  
1.  Appuyez sur la touche F5 pour exécuter le projet et le déployer sur SharePoint.  
  
2.  Cliquez sur le bouton **Accueil**, puis **Documents partagés** dans la barre de lancement rapide pour afficher la liste Documents partagés sur le site SharePoint.  
  
3.  Pour représenter les notes de frais de cet exemple, téléchargez de nouveaux documents dans la liste Documents en cliquant sur le lien **Documents** dans l'onglet **Outils de bibliothèque** en haut de la page, puis en cliquant sur le bouton **Télécharger un document** dans le ruban.  
  
4.  Après avoir téléchargé certains documents, instancier le flux de travail en choisissant le lien **Bibliothèque** sous l'onglet **LibraryTools** en haut de la page puis en choisissant le bouton **Paramètres de la bibliothèque** sur le ruban outil.  
  
5.  Sur la page **Paramètres de la bibliothèque de documents**, cliquez sur le lien **Paramètres du flux de travail** dans la section **Autorisations et gestion**.  
  
6.  Dans la page **Paramètres du flux de travail**, cliquez sur le lien **Ajouter un flux de travail**.  
  
7.  Dans la page **Ajouter un flux de travail**, sélectionnez le flux de travail intitulé **ExpenseReport \- Workflow1**, donnez\-lui un nom tel que TestNotedefrais, puis cliquez sur **Suivant**.  
  
     Le formulaire d'association de flux de travail s'affiche.  Utilisez\-le pour signaler le montant limite des frais.  
  
8.  Sous la forme d'association, entrez **1000** dans la zone **Limite d'approbation automatique**, puis cliquez sur le bouton **Associer le flux de travail**.  
  
9. Cliquez sur le bouton **Accueil** pour revenir à la page d'accueil SharePoint.  
  
10. Cliquez sur le lien **Documents partagés** dans la barre de lancement rapide.  
  
11. Choisissez l'un des documents téléchargés pour afficher une flèche déroulante, choisissez\-le, puis choisissez l'élément **Flux de travail**.  
  
12. Cliquez sur l'image en regard du flux de travail TestNotedefrais pour afficher le formulaire d'initiation correspondant.  
  
13. Dans la zone de texte **Total des dépenses**, entrez une valeur supérieure à 1000, puis cliquez sur le bouton **Démarrer le flux de travail**.  
  
     Cela aura pour effet d'ajouter une tâche à la liste des tâches dès qu'une note de frais dépassera la limite fixée.  Une colonne intitulée **TestNotedefrais** contenant la valeur **Terminé** sera également insérée dans l'élément note de frais à l'intérieur de la liste Documents partagés.  
  
14. Réappliquez les étapes 11 à 13 à d'autres documents dans la liste Documents partagés. Le nombre exact de documents n'a pas d'importance.  
  
15. Affichez la page d'application du résumé de la note de frais en entrant l'URL suivante dans un navigateur Web : **http:\/\/***SystemName* **\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**.  
  
     La page en question contient un récapitulatif de toutes les notes de frais supérieures au seuil limite fixé, indique de combien il a été dépassé à chaque fois et calcule le montant total de toutes les notes de frais.  
  
## Étapes suivantes  
 Pour plus d'informations au sujet des pages d'application SharePoint, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Pour savoir comment définir le contenu des pages SharePoint à l'aide du Concepteur Web de Visual Studio, consultez les rubriques suivantes :  
  
-   [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Comment : créer une page d'application](../sharepoint/how-to-create-an-application-page.md)   
 [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  