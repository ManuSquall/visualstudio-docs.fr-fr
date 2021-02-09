---
title: Créer un flux de travail avec des formulaires d’association et d’initiation
description: Dans cette procédure pas à pas SharePoint, créez un flux de travail séquentiel de base qui incorpore l’utilisation des formulaires d’association et d’initiation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cb759b155b119c29f20a39cdbf35338ec5a305b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847737"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation
  Cette procédure pas à pas montre comment créer un flux de travail séquentiel de base qui incorpore l’utilisation des formulaires d’association et d’initiation. Il s’agit de formulaires ASPX qui permettent d’ajouter des paramètres à un flux de travail lorsqu’il est associé pour la première fois par l’administrateur SharePoint (le formulaire d’association) et lorsque le flux de travail est démarré par l’utilisateur (formulaire d’initiation).

 Cette procédure pas à pas décrit un scénario dans lequel un utilisateur souhaite créer un flux de travail d’approbation pour les notes de frais qui ont les exigences suivantes :

- Lorsque le flux de travail est associé à une liste, l’administrateur est invité à entrer une limite en dollars pour les notes de frais.

- Les employés chargent leurs notes de frais dans la liste documents partagés, démarrent le flux de travail, puis entrent le montant total des dépenses dans le formulaire d’initiation du flux de travail.

- Si le total d’un rapport de frais d’un employé dépasse la limite prédéfinie par l’administrateur, une tâche est créée pour que le responsable de l’employé approuve la note de frais. Toutefois, si le total du rapport de frais d’un employé est inférieur ou égal à la limite de dépense, un message approuvé automatiquement est écrit dans la liste historique du flux de travail.

  Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de flux de travail séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Création d’une planification de flux de travail.

- Gestion des événements d’activité de flux de travail.

- Création d’une association de flux de travail et de formulaires d’initiation.

- Association du flux de travail.

- Démarrage manuel du flux de travail.

> [!NOTE]
> Bien que cette procédure pas à pas utilise un projet de workflow séquentiel, le processus est le même pour les flux de travail d’ordinateur d’État.
>
> En outre, il se peut que votre ordinateur affiche des noms ou des emplacements différents pour certains éléments de l' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] interface utilisateur dans les instructions suivantes. L' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] édition dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Créer un projet de flux de travail séquentiel SharePoint
 Commencez par créer un projet de workflow séquentiel dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Un workflow séquentiel est une série d’étapes qui s’exécutent dans l’ordre jusqu’à ce que la dernière activité se termine. Dans cette procédure, vous allez créer un flux de travail séquentiel qui s’applique à la liste documents partagés dans SharePoint. L’Assistant du flux de travail vous permet d’associer le flux de travail au site ou à la définition de liste et vous permet de déterminer à quel moment le flux de travail démarrera.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Pour créer un projet de flux de travail séquentiel SharePoint

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** .

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet **modèles** , choisissez le modèle projet de **projet SharePoint 2010** .

4. Dans la zone **nom** , entrez **ExpenseReport** , puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , choisissez la case **d’option déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.

     Cette étape définit également le niveau de confiance de la solution en tant que solution de batterie, qui est la seule option disponible pour les projets de Workflow.

6. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

7. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

8. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

9. Dans le volet **modèles** , choisissez **Workflow séquentiel (solution de batterie uniquement)** , puis cliquez sur le bouton **Ajouter** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

10. Dans la page **spécifier le nom du flux de travail pour le débogage** , acceptez le nom par défaut (**ExpenseReport-Workflow1**). Conservez la valeur de type de modèle de flux de travail par défaut (**List Workflow)**. Choisissez le bouton **Suivant**.

11. Dans la page **voulez-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage ?** , désactivez la case qui associe automatiquement votre modèle de flux de travail si elle est activée.

     Cette étape vous permet d’associer manuellement le flux de travail à la liste documents partagés, qui affiche le formulaire d’association.

12. Cliquez sur le bouton **Terminer**.

## <a name="add-an-association-form-to-the-workflow"></a>Ajouter un formulaire d’association au flux de travail
 Ensuite, créez un. Formulaire d’association ASPX qui apparaît lorsque l’administrateur SharePoint associe d’abord le flux de travail à un document de note de frais.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Pour ajouter un formulaire d’association au flux de travail

1. Dans **Explorateur de solutions**, choisissez le nœud **Workflow1** .

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément** .

3. Dans la vue de l’arborescence de la boîte de dialogue, développez **Visual C#** ou **Visual Basic** (selon le langage de votre projet), développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans la liste des modèles, choisissez le modèle de **formulaire d’association de flux de travail** .

5. Dans la zone de texte **nom** , entrez **ExpenseReportAssocForm. aspx**.

6. Cliquez sur le bouton **Ajouter** pour ajouter le formulaire au projet.

## <a name="designing-and-coding-the-association-form"></a>Conception et codage du formulaire d’association
 Dans cette procédure, vous introduisez des fonctionnalités dans le formulaire Association en y ajoutant des contrôles et du code.

#### <a name="to-design-and-code-the-association-form"></a>Pour concevoir et coder le formulaire d’association

1. Dans le formulaire d’Association (ExpenseReportAssocForm. aspx), recherchez l' `asp:Content` élément qui possède `ID="Main"` .

2. Directement après la première ligne de cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte qui demandent la limite d’approbation des dépenses (*AutoApproveLimit*) :

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Développez le fichier **ExpenseReportAssocForm. aspx** dans **Explorateur de solutions** pour afficher ses fichiers dépendants.

    > [!NOTE]
    > Si votre projet se trouve dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , vous devez cliquer sur le bouton **Afficher tous les fichiers** pour effectuer cette étape.

4. Ouvrez le menu contextuel du fichier ExpenseReportAssocForm. aspx, puis choisissez **afficher le code**.

5. Remplacez la `GetAssociationData` méthode par :

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Ajouter un formulaire d’initiation au flux de travail
 Ensuite, créez le formulaire d’initiation qui s’affiche lorsque les utilisateurs exécutent le flux de travail par rapport à leurs notes de frais.

#### <a name="to-create-an-initiation-form"></a>Pour créer un formulaire d’initiation

1. Dans **Explorateur de solutions**, choisissez le nœud **Workflow1** .

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément** .

3. Dans la vue de l’arborescence de la boîte de dialogue, développez **Visual C#** ou **Visual Basic**  (selon le langage de votre projet), développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans la liste des modèles, choisissez le modèle de **formulaire d’initiation de flux de travail** .

5. Dans la zone de texte **nom** , entrez **ExpenseReportInitForm. aspx**.

6. Cliquez sur le bouton **Ajouter** pour ajouter le formulaire au projet.

## <a name="designing-and-coding-the-initiation-form"></a>Conception et codage du formulaire d’initiation
 Introduisez ensuite des fonctionnalités dans le formulaire d’initiation en y ajoutant des contrôles et du code.

#### <a name="to-code-the-initiation-form"></a>Pour coder le formulaire d’initiation

1. Dans le formulaire d’initiation (ExpenseReportInitForm. aspx), recherchez l' `asp:Content` élément qui contient `ID="Main"` .

2. Directement après la première ligne de cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte qui affichent la limite d’approbation des dépenses (*AutoApproveLimit*) qui a été entrée dans le formulaire d’association, et une autre étiquette et zone de texte pour demander le total des dépenses (*ExpenseTotal*) :

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Développez le fichier **ExpenseReportInitForm. aspx** dans **Explorateur de solutions** pour afficher ses fichiers dépendants.

4. Ouvrez le menu contextuel du fichier ExpenseReportInitForm. aspx, puis choisissez **afficher le code**.

5. Remplacez la `Page_Load` méthode par l’exemple suivant :

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Remplacez la `GetInitiationData` méthode par l’exemple suivant :

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize le flux de travail
 Ensuite, personnalisez le flux de travail. Plus tard, vous allez associer deux formulaires au flux de travail.

#### <a name="to-customize-the-workflow"></a>Pour personnaliser le flux de travail

1. Affichez le flux de travail dans le concepteur de workflow en ouvrant Workflow1 dans le projet.

2. Dans la **boîte à outils**, développez le nœud **Windows Workflow v 3.0** et recherchez l’activité **IfElse** .

3. Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :

    - Ouvrez le menu contextuel de l’activité **IfElse** , choisissez **copier**, ouvrez le menu contextuel de la ligne sous l’activité **onWorkflowActivated1** dans le concepteur de flux de travail, puis choisissez **coller**.

    - Faites glisser l’activité **IfElse** de la **boîte à outils** et connectez-la à la ligne sous l’activité **onWorkflowActiviated1** dans le concepteur de Workflow.

4. Dans la boîte à outils, développez le nœud **flux de travail SharePoint** et recherchez l’activité **CreateTask** .

5. Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :

    - Ouvrez le menu contextuel de l’activité **CreateTask** , choisissez **copier**, ouvrez le menu contextuel pour l’une des deux **activités Drop ici** dans **IfElseActivity1** dans le concepteur de flux de travail, puis choisissez **coller**.

    - Faites glisser l’activité **CreateTask** de la **boîte à outils** vers l’une des deux **activités Drop ici** dans **IfElseActivity1**.

6. Dans la fenêtre **Propriétés** , entrez une valeur de propriété de *taskToken* pour la propriété **CorrelationToken** .

7. Développez la propriété **CorrelationToken** en choisissant le signe plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) en regard de celle-ci.

8. Choisissez la flèche déroulante de la sous-propriété **OwnerActivityName** et définissez la valeur *Workflow1* .

9. Choisissez la propriété **taskId** , puis cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) pour afficher la boîte de dialogue de **Propriétés de liaison** .

10. Choisissez l’onglet **lier à un nouveau membre** , choisissez la case d’option **créer un champ** , puis cliquez sur le bouton **OK** .

11. Choisissez la propriété **TaskProperties (propriétés** , puis cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) pour afficher la boîte de dialogue **lier la propriété** .

12. Choisissez l’onglet **lier à un nouveau membre** , choisissez la case d’option **créer un champ** , puis cliquez sur le bouton **OK** .

13. Dans la **boîte à outils**, développez le nœud **flux de travail SharePoint** , puis recherchez l’activité **LogToHistoryListActivity** .

14. Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :

    - Ouvrez le menu contextuel de l’activité **LogToHistoryListActivity** , choisissez **copier**, ouvrez le menu contextuel pour l’autre zone **déposer activités ici** dans **IfElseActivity1** dans le concepteur de flux de travail, puis choisissez **coller**.

    - Faites glisser l’activité **LogToHistoryListActivity** de la **boîte à outils** et déposez-la sur l’autre zone **déposer activités ici** dans **IfElseActivity1**.

## <a name="add-code-to-the-workflow"></a>Ajouter du code au workflow
 Ensuite, ajoutez du code au workflow pour lui fournir des fonctionnalités.

#### <a name="to-add-code-to-the-workflow"></a>Pour ajouter du code au workflow

1. Ouvrez le menu contextuel de l’activité **createTask1** dans le concepteur de flux de travail, puis choisissez **afficher le code**.

2. Ajoutez la méthode suivante :

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > Dans le code, remplacez `somedomain\\someuser` par un nom de domaine et d’utilisateur pour lequel une tâche sera créée, telle que « `Office\\JoeSch` ». Pour les tests, il est plus facile d’utiliser le compte que vous développez avec.

3. Sous la `MethodInvoking` méthode, ajoutez l’exemple suivant :

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. Dans le concepteur de flux de travail, choisissez l’activité **ifElseBranchActivity1** .

5. Dans la fenêtre **Propriétés** , choisissez la flèche déroulante de la propriété **condition** , puis définissez la valeur de la *condition de code* .

6. Développez la propriété **condition** en choisissant le signe plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) en regard de celle-ci, puis définissez sa valeur sur *checkApprovalNeeded*.

7. Dans le concepteur de flux de travail, ouvrez le menu contextuel de l’activité **logToHistoryListActivity1** , puis choisissez **générer des gestionnaires** pour générer une méthode vide pour l' `MethodInvoking` événement.

8. Remplacez le `MethodInvoking` code par ce qui suit :

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Appuyez sur la touche **F5** pour déboguer le programme.

     Cela a pour fonction de compiler l’application, de l’empaqueter, de la déployer, d’activer ses fonctionnalités, de recycler le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications, puis de démarrer le navigateur à l’emplacement spécifié dans la propriété **URL du site** .

## <a name="associating-the-workflow-to-the-documents-list"></a>Association du flux de travail à la liste de documents
 Ensuite, affichez le formulaire d’association de flux de travail en associant le flux de travail à la liste **SharedDocuments** sur le site SharePoint.

#### <a name="to-associate-the-workflow"></a>Pour associer le flux de travail

1. Choisissez le lien **documents partagés** dans la barre de lancement rapide.

2. Cliquez sur le lien **bibliothèque** sous l’onglet **outils de bibliothèque** , puis sur le bouton du ruban paramètres de la **bibliothèque** .

3. Dans la section **autorisations et gestion** , choisissez le lien **paramètres de flux de travail** , puis choisissez le lien **Ajouter un flux de travail** dans la page **flux** de travail.

4. Dans la liste supérieure de la page Paramètres de flux de travail, choisissez le modèle **ExpenseReport-Workflow1** .

5. Dans le champ suivant, entrez **ExpenseReportWorkflow** , puis choisissez le bouton **suivant** .

     Cela permet d’associer le flux de travail à la liste **documents partagés** et d’afficher le formulaire d’association de flux de travail.

6. Dans la zone de texte **limite d’approbation automatique** , entrez **1200** , puis choisissez le bouton **associer le flux de travail** .

## <a name="start-the-workflow"></a>Démarrer le flux de travail
 Ensuite, associez le flux de travail à l’un des documents de la liste **documents partagés** pour afficher le formulaire d’initiation de flux de travail.

#### <a name="to-start-the-workflow"></a>Pour démarrer le flux de travail

1. Sur la page SharePoint, choisissez le bouton **démarrage** .

2. Choisissez le lien **documents partagés** dans la barre de lancement rapide pour afficher la liste **documents partagés** .

3. Choisissez le lien **documents** sous l’onglet **outils de bibliothèque** en haut de la page, puis choisissez le bouton **Télécharger un document** sur le ruban pour télécharger un nouveau document dans la liste **documents partagés** .

4. Dans la boîte de dialogue **Télécharger un document** , cliquez sur le bouton **Parcourir** , choisissez un fichier de document, cliquez sur le bouton **ouvrir** , puis choisissez le bouton **OK** .

     Vous pouvez modifier les paramètres du document dans cette boîte de dialogue, mais les conserver aux valeurs par défaut en choisissant le bouton **Enregistrer** .

5. Choisissez le document chargé, choisissez la flèche déroulante qui s’affiche, puis choisissez l’élément **flux de travail** .

6. Choisissez l’image en regard de ExpenseReportWorkflow.

     Le formulaire d’initiation de flux de travail s’affiche. (Notez que la valeur affichée dans la zone **limite d’approbation automatique** est en lecture seule, car elle a été entrée dans le formulaire Association.)

7. Dans la zone de texte **total des dépenses** , entrez **1600**, puis choisissez le bouton Démarrer le **flux de travail** .

     La liste **documents partagés** s’affiche à nouveau. Une nouvelle colonne nommée **ExpenseReportWorkflow** avec la valeur **Completed** est ajoutée à l’élément que le workflow vient de démarrer.

8. Choisissez la flèche déroulante en regard du document téléchargé, puis choisissez l’élément **flux de travail** pour afficher la page État du flux de travail. Choisissez la valeur **terminé** sous **workflows terminés**. La tâche est indiquée sous la section **tâches** .

9. Choisissez le titre de la tâche pour afficher ses détails sur la tâche.

10. Revenez à la liste **SharedDocuments** et redémarrez le flux de travail à l’aide du même document ou d’un autre document.

11. Entrez un montant sur la page d’initiation inférieure ou égale à la quantité entrée sur la page Association (**1200**).

     Dans ce cas, une entrée de la liste historique est créée à la place d’une tâche. L’entrée s’affiche dans la section **historique du flux** de travail de la page État du flux de travail. Notez le message dans la colonne **résultat** de l’événement historique. Il contient le texte entré dans l' `logToHistoryListActivity1.MethodInvoking` événement qui inclut le montant qui a été approuvé automatiquement.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur la création de modèles de flux de travail, consultez les rubriques suivantes :

- Pour en savoir plus sur les flux de travail SharePoint, consultez [workflows dans Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Procédure pas à pas : ajouter une page d’application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
