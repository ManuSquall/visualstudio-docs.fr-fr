---
title: 'Procédure pas à pas : Ajout d’une Page d’Application à un flux de travail | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ed3278a237633cbf7f15806fa0efa9b3bc33bb6
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Procédure pas à pas : ajout d'une page d'application à un flux de travail
  Cette procédure pas à pas montre comment ajouter une page d’application qui affiche des données dérivées d’un flux de travail dans un projet de flux de travail. Il repose sur le projet décrit dans la rubrique [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’une page d’application ASPX à un projet de flux de travail SharePoint.  
  
-   Obtention de données à partir du projet de flux de travail et la manipulation.  
  
-   Affichage des données dans une table dans la page de l’application.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Vous devez également terminer le projet dans la rubrique [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## <a name="amending-the-workflow-code"></a>Modifiant le Code de flux de travail  
 Tout d’abord, ajoutez une ligne de code pour le flux de travail pour définir la valeur de la colonne de résultat à la quantité de la note de frais. Cette valeur est utilisée ultérieurement dans le calcul de synthèse d’état dépenses.  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Pour définir la valeur de la colonne de résultat dans le flux de travail  
  
1.  Charger le projet terminé à partir de la rubrique [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Ouvrez le code de Workflow1.cs ou Workflow1.vb (selon votre langage de programmation).  
  
3.  Au bas de la `createTask1_MethodInvoking` méthode, ajoutez le code suivant :  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>Création d’une Page d’Application  
 Ensuite, ajoutez un formulaire ASPX au projet. Cet écran affiche les données obtenues à partir du projet de flux de travail Rapport dépenses. Pour ce faire, vous allez ajouter une page d’application. Une page d’application utilise la même page maître que les autres pages SharePoint, ce qui signifie que qu’elle sera semblable à des autres pages sur le site SharePoint.  
  
#### <a name="to-add-an-application-page-to-the-project"></a>Pour ajouter une page d’application au projet  
  
1.  Choisissez le projet ExpenseReport, puis, dans la barre de menus, **projet**, **ajouter un nouvel élément**.  
  
2.  Dans le **modèles** volet, choisissez la **Page Application** modèle, le nom par défaut pour l’élément de projet (**ApplicaitonPage1.aspx**) et choisissez la **Ajouter** bouton.  
  
3.  Dans le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de ApplicationPage1.aspx, remplacez la `PlaceHolderMain` section avec les éléments suivants :  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Ce code ajoute une table à la page avec un titre.  
  
4.  Ajouter un titre à la page d’application en remplaçant la `PlaceHolderPageTitleInTitleArea` section avec les éléments suivants :  
  
    ```aspx-csharp  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>Codage de la Page d’Application  
 Ensuite, ajoutez le code à la page d’application du résumé de rapport dépenses. Lorsque vous ouvrez la page, le code d’analyse de la liste des tâches dans SharePoint pour les dépenses ayant dépassé la limite de dépense allouée. Le rapport répertorie chaque élément ainsi que la somme des frais.  
  
#### <a name="to-code-the-application-page"></a>Code de la page d’application  
  
1.  Choisissez le **ApplicationPage1.aspx** nœud, puis, dans la barre de menus, choisissez **vue**, **Code** pour afficher le code-behind de la page d’application.  
  
2.  Remplacez le **à l’aide de** ou **importation** instructions (selon votre langage de programmation) en haut de la classe avec les éléments suivants :  
  
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
    >  Veillez à remplacer « TestServer » dans le code avec le nom de serveur qui exécute SharePoint valide.  
  
## <a name="testing-the-application-page"></a>Test de la Page d’Application  
 Ensuite, déterminez si la page d’application affiche les données de frais correctement.  
  
#### <a name="to-test-the-application-page"></a>Pour tester la page d’application  
  
1.  Choisissez la touche F5 pour exécuter et déployer le projet vers SharePoint.  
  
2.  Choisissez le **accueil** bouton, puis choisissez le **Documents partagés** lien dans la barre de lancement rapide pour afficher la liste de Documents partagés sur le site SharePoint.  
  
3.  Pour représenter les notes de frais de cet exemple, téléchargez de nouveaux documents dans la liste des Documents en choisissant le **Documents** lien sur le **outils de bibliothèque** onglet en haut de la page, puis en choisissant le  **Télécharger un Document** bouton dans la barre d’outils.  
  
4.  Après avoir téléchargé des documents, instanciez le flux de travail en choisissant le **bibliothèque** lien sur le **outils de bibliothèque** onglet en haut de la page, puis en sélectionnant le **paramètres de la bibliothèque**bouton dans la barre d’outils.  
  
5.  Dans le **paramètres de la bibliothèque** page, choisissez la **les paramètres de flux de travail** lien dans le **autorisations et gestion** section.  
  
6.  Dans le **les paramètres de flux de travail** page, choisissez la **ajouter un flux de travail** lien.  
  
7.  Dans le **ajouter un flux de travail** page, choisissez la **ExpenseReport - Workflow1** flux de travail, entrez un nom pour le flux de travail, tel que **TestNotedefrais**, puis choisissez le **Suivant** bouton.  
  
     Le formulaire d’Association de flux de travail s’affiche. Il permet de signaler le montant de limite de dépense.  
  
8.  Dans le formulaire d’Association, entrez **1000** dans les **limite d’approbation automatique** zone, puis choisissez le **associer le flux de travail** bouton.  
  
9. Choisissez le **domestique** bouton pour revenir à la page d’accueil SharePoint.  
  
10. Choisissez le **Documents partagés** lien dans la barre de lancement rapide.  
  
11. Choisissez un des documents téléchargés pour afficher une flèche de déroulement, sélectionnez-le, puis choisissez le **Workflows** élément.  
  
12. Sélectionnez l’image en regard de la TestNotedefrais pour afficher le formulaire d’Initiation de flux de travail.  
  
13. Dans le **Total des dépenses** zone de texte, entrez une valeur qui est supérieure à 1 000, puis choisissez le **démarrer le flux de travail** bouton.  
  
     Lorsqu’une note de frais dépasse le montant de frais alloué, une tâche est ajoutée à la liste des tâches. Une colonne nommée **TestNotedefrais** avec la valeur **terminé** est également ajouté à l’élément de rapport de dépenses dans la liste de Documents partagés.  
  
14. Répétez les étapes 11 à 13 avec d’autres documents dans la liste de Documents partagés. (Le nombre exact de documents n’est pas important).  
  
15. Afficher la page d’application du résumé de rapport frais en ouvrant l’URL suivante dans un navigateur Web : **http://***Nom_système***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     La page de résumé du rapport dépenses répertorie tous les États de dépenses qui a dépassé la quantité allouée, le montant par qu'ils dépassaient et la quantité totale de tous les rapports.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur les pages d’application SharePoint, consultez [création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Vous pouvez en savoir plus sur la conception de contenu de la page SharePoint à l’aide du Concepteur Web visuel dans Visual Studio à partir de ces rubriques :  
  
-   [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Comment : créer une Page d’Application](../sharepoint/how-to-create-an-application-page.md)   
 [Création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  