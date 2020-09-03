---
title: 'Procédure pas à pas : ajouter une page d’application à un flux de travail | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f54914e6676e0cc2400fa04ebb089fac08f58c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015495"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Procédure pas à pas : ajouter une page d’application à un flux de travail
  Cette procédure pas à pas montre comment ajouter une page d’application qui affiche des données dérivées d’un flux de travail à un projet de Workflow. Il s’appuie sur le projet décrit dans la rubrique [procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d’une page d’application ASPX à un projet de flux de travail SharePoint.

- Obtention de données à partir du projet de workflow et manipulation de celles-ci.

- Affichage des données dans une table sur la page de l’application.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

- Vous devez également terminer le projet dans la rubrique [procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend le code de workflow
 Tout d’abord, ajoutez une ligne de code au flux de travail pour définir la valeur de la colonne de résultat sur le montant de la note de frais. Cette valeur est utilisée ultérieurement dans le calcul du résumé de l’état des dépenses.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Pour définir la valeur de la colonne de résultat dans le flux de travail

1. Chargez le projet terminé à partir de la rubrique [procédure pas à pas : création d’un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Ouvrez le code pour *Workflow1.cs* ou *Workflow1. vb* (en fonction de votre langage de programmation).

3. En bas de la `createTask1_MethodInvoking` méthode, ajoutez le code suivant :

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Page créer une application
 Ensuite, ajoutez un formulaire ASPX au projet. Ce formulaire affiche les données obtenues à partir du projet de flux de travail des notes de frais. Pour ce faire, vous allez ajouter une page d’application. Une page d’application utilise la même page maître que les autres pages SharePoint, ce qui signifie qu’elle doit ressembler à d’autres pages sur le site SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Pour ajouter une page d’application au projet

1. Choisissez le projet ExpenseReport, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

2. Dans le volet **modèles** , choisissez le modèle de **page d’application** , utilisez le nom par défaut de l’élément de projet (**ApplicationPage1. aspx**), puis cliquez sur le bouton **Ajouter** .

3. Dans le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de ApplicationPage1. aspx, remplacez la `PlaceHolderMain` section par ce qui suit :

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Ce code ajoute un tableau à la page avec un titre.

4. Ajoutez un titre à la page de l’application en remplaçant la `PlaceHolderPageTitleInTitleArea` section par ce qui suit :

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Code de la page d’application
 Ensuite, ajoutez du code à la page de l’application de synthèse des notes de frais. Lorsque vous ouvrez la page, le code analyse la liste des tâches dans SharePoint pour déterminer les dépenses qui ont dépassé la limite de dépense allouée. Le rapport répertorie chaque élément ainsi que la somme des dépenses.

#### <a name="to-code-the-application-page"></a>Pour coder la page de l’application

1. Choisissez le nœud **ApplicationPage1. aspx** , puis, dans la barre de menus, choisissez **Afficher**  >  le**code** pour afficher le code derrière la page de l’application.

2. Remplacez les instructions **using** ou **Import** (en fonction de votre langage de programmation) en haut de la classe par les éléments suivants :

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

3. Ajoutez le code suivant à la méthode `Page_Load` :

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
    > Veillez à remplacer « TestServer » dans le code par le nom d’un serveur valide qui exécute SharePoint.

## <a name="test-the-application-page"></a>Tester la page de l’application
 Ensuite, déterminez si la page d’application affiche correctement les données de la dépense.

#### <a name="to-test-the-application-page"></a>Pour tester la page d’application

1. Appuyez sur la touche **F5** pour exécuter et déployer le projet sur SharePoint.

2. Choisissez le bouton **démarrage** , puis cliquez sur le lien **documents partagés** dans la barre de lancement rapide pour afficher la liste documents partagés sur le site SharePoint.

3. Pour représenter des notes de frais pour cet exemple, téléchargez de nouveaux documents dans la liste documents en choisissant le lien **documents** sous l’onglet **LibraryTools** en haut de la page, puis en choisissant le bouton **Télécharger un document** sur le ruban d’outils.

4. Après avoir téléchargé des documents, instanciez le flux de travail en cliquant sur le lien de la **bibliothèque** sous l’onglet **LibraryTools** en haut de la page, puis en choisissant le bouton Paramètres de la **bibliothèque** sur le ruban d’outils.

5. Dans la page Paramètres de la **bibliothèque de documents** , choisissez le lien paramètres de flux de **travail** dans la section **autorisations et gestion** .

6. Dans la page **paramètres de flux de travail** , choisissez le lien **Ajouter un flux de travail** .

7. Dans la page **Ajouter un flux** de travail, choisissez le flux de travail **ExpenseReport-Workflow1** , entrez un nom pour le flux de travail, tel que **ExpenseTest**, puis choisissez le bouton **suivant** .

    Le formulaire d’association de flux de travail s’affiche. Utilisez-le pour signaler le montant de la limite de dépense.

8. Dans le formulaire Association, entrez **1000** dans la zone **limite d’approbation automatique** , puis choisissez le bouton **associer le flux de travail** .

9. Cliquez sur le bouton **démarrage** pour revenir à la page d’espace SharePoint.

10. Choisissez le lien **documents partagés** dans la barre de lancement rapide.

11. Choisissez l’un des documents téléchargés pour afficher une flèche déroulante, choisissez-le, puis choisissez l’élément **flux de travail** .

12. Choisissez l’image en regard de ExpenseTest pour afficher le formulaire d’initiation de flux de travail.

13. Dans la zone de texte **total des dépenses** , entrez une valeur supérieure à 1000, puis choisissez le bouton **Démarrer le flux de travail** .

     Quand une dépense signalée dépasse le montant des dépenses allouées, une tâche est ajoutée au Liste des tâches. Une colonne nommée **ExpenseTest** avec la valeur **Completed** est également ajoutée à l’élément de note de frais dans la liste documents partagés.

14. Répétez les étapes 11-13 avec d’autres documents dans la liste documents partagés. (Le nombre exact de documents n’est pas important.)

15. Affichez la page application résumée des notes de frais en ouvrant l’URL suivante dans un navigateur Web : **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     La page Résumé de la note de frais répertorie tous les États de dépenses qui ont dépassé le montant alloué, le montant qu’ils ont dépassé et le montant total de tous les rapports.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur les pages d’application SharePoint, consultez [créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Pour plus d’informations sur la création de contenu de page SharePoint à l’aide de Visual Web Designer dans Visual Studio, consultez les rubriques suivantes :

- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Comment : créer une page d’application](../sharepoint/how-to-create-an-application-page.md)
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)