---
title: 'Procédure pas à pas : Création d’un Workflow avec les formulaires d’Association et Initiation | Microsoft Docs'
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
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6aafde6fed0a1f1722c2d355499523114aaaa00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873875"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Procédure pas à pas : Créer un flux de travail avec des formulaires d’association et d’initiation
  Cette procédure pas à pas montre comment créer un workflow séquentiel de base qui incorpore l’utilisation des formulaires d’association et d’initiation. Il s’agit de formulaires ASPX permettant d’activer les paramètres à ajouter à un flux de travail lorsqu’il est tout d’abord associée par l’administrateur SharePoint (formulaire d’association), et lorsque le workflow est démarré par l’utilisateur (le formulaire d’initiation).  
  
 Cette procédure pas à pas décrit un scénario où un utilisateur souhaite créer un workflow d’approbation des notes de frais qui exige les éléments suivants :  
  
- Lorsque le flux de travail est associé à une liste, l’administrateur est invité avec un formulaire d’association où ils entrent une limite de dollar des notes de frais.  
  
- Employés charger leurs rapports de dépenses dans la liste de Documents partagés, démarrer le flux de travail, puis entrez le coût total dans le formulaire d’initiation du flux de travail.  
  
- Si une note de frais des employés total dépasse la limite prédéfinie de l’administrateur, une tâche est créée pour le Gestionnaire de l’employé approuver la note de frais. Toutefois, si le total de rapports de dépenses d’un employé est inférieur ou égal à la limite de dépense, un message d’auto-approuvés est écrite dans l’historique du flux de travail.  
  
  Cette procédure pas à pas décrit les tâches suivantes :  
  
- Création d’un projet de workflow séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Création d’une planification de flux de travail.  
  
- Gestion des événements d’activité de flux de travail.  
  
- Création des formulaires d’association et d’initiation du flux de travail.  
  
- Associer le flux de travail.  
  
- Démarrage manuel du flux de travail.  
  
> [!NOTE]  
>  Bien que cette procédure pas à pas utilise un projet de workflow séquentiel, le processus est identique pour les workflows machine à états.  
>   
>  En outre, votre ordinateur peut afficher des noms différents ou des emplacements de certains de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] les éléments d’interface utilisateur dans les instructions suivantes. Le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] édition dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Créer un projet de flux de travail séquentiel SharePoint
 Tout d’abord, créez un projet de flux de travail séquentiel dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Un workflow séquentiel est une série d’étapes qui s’exécute dans l’ordre jusqu'à la fin de la dernière activité. Dans cette procédure, vous allez créer un workflow séquentiel qui s’applique à la liste de Documents partagés dans SharePoint. L’Assistant flux de travail vous permet d’associer le flux de travail avec le site ou la définition de liste et vous permet de déterminer quand le flux de travail démarre.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Pour créer un projet de flux de travail séquentiel SharePoint  
  
1.  Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.  
  
2.  Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.  
  
3.  Dans le **modèles** volet, choisissez le **projet SharePoint 2010** modèle de projet.  
  
4.  Dans le **nom** , entrez **ExpenseReport** , puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
5.  Dans le **spécifier le niveau de site et de sécurité pour le débogage** page, choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton pour accepter le site par défaut et le niveau de confiance.  
  
     Cette étape définit également le niveau de confiance pour la solution en tant que solution de batterie de serveurs, ce qui est la seule option disponible pour les projets de flux de travail.  
  
6.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.  
  
7.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.  
  
8.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
9. Dans le **modèles** volet, choisissez **Workflow séquentiel (Solution de batterie uniquement)** modèle, puis choisissez le **ajouter** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
10. Dans le **spécifier le nom de flux de travail pour le débogage** page, acceptez le nom par défaut (**ExpenseReport - Workflow1**). Conservez la valeur de type de modèle de flux de travail par défaut (**liste de flux de travail)**. Choisissez le bouton **Suivant**.  
  
11. Dans le **voulez-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage ?** page, désactivez la case qui associe automatiquement votre modèle de flux de travail si elle est activée.  
  
     Cette étape vous permet d’associer manuellement le flux de travail avec la liste de Documents partagés par la suite qui affiche le formulaire d’association.  
  
12. Choisissez le **Terminer** bouton.  
  
## <a name="add-an-association-form-to-the-workflow"></a>Ajouter un formulaire d’association pour le flux de travail
 Ensuite, créez un. Formulaire d’association ASPX qui apparaît lorsque l’administrateur SharePoint associe tout d’abord le flux de travail à un document de bilan d’exploitation.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Pour ajouter un formulaire d’association pour le flux de travail  
  
1.  Choisissez le **Workflow1** nœud **l’Explorateur de solutions**.  
  
2.  Dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément** pour afficher le **ajouter un nouvel élément** boîte de dialogue.  
  
3.  Dans la vue arborescence de la boîte de dialogue, développez le **Visual C#** ou **Visual Basic** (selon votre langage de projet), développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans la liste des modèles, choisissez le **formulaire d’Association de flux de travail** modèle.  
  
5.  Dans le **nom** texte, entrez **ExpenseReportAssocForm.aspx**.  
  
6.  Choisissez le **ajouter** pour ajouter le formulaire au projet.  
  
## <a name="designing-and-coding-the-association-form"></a>Conception et codage du formulaire association
 Dans cette procédure, vous introduisez des fonctionnalités au formulaire association en y ajoutant des contrôles et du code à.  
  
#### <a name="to-design-and-code-the-association-form"></a>Pour concevoir et coder le formulaire d’association  
  
1.  Dans le formulaire d’association (ExpenseReportAssocForm.aspx), localisez le `asp:Content` élément qui a `ID="Main"`.  
  
2.  Directement après la première ligne dans cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte qui invite à entrer le plafond de dépenses (*AutoApproveLimit*) :  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Développez le **ExpenseReportAssocForm.aspx** fichier **l’Explorateur de solutions** pour afficher ses fichiers dépendants.  
  
    > [!NOTE]  
    >  Si votre projet se trouve dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], vous devez choisir le **afficher tous les fichiers** bouton pour effectuer cette étape.  
  
4.  Ouvrez le menu contextuel pour le fichier ExpenseReportAssocForm.aspx et choisissez **afficher le Code**.  
  
5.  Remplacez le `GetAssociationData` méthode avec :  
  
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
 Ensuite, créez le formulaire d’initiation qui s’affiche quand les utilisateurs exécutent le flux de travail par rapport à leurs notes de frais.  
  
#### <a name="to-create-an-initiation-form"></a>Pour créer un formulaire d’initiation  
  
1.  Choisissez le **Workflow1** nœud **l’Explorateur de solutions**.  
  
2.  Dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément** afficher le **ajouter un nouvel élément** boîte de dialogue.  
  
3.  Dans la vue arborescence de la boîte de dialogue, développez le **Visual C#** ou **Visual Basic** (selon votre langage de projet), développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans la liste des modèles, choisissez le **formulaire d’Initiation du flux de travail** modèle.  
  
5.  Dans le **nom** texte, entrez **ExpenseReportInitForm.aspx**.  
  
6.  Choisissez le **ajouter** pour ajouter le formulaire au projet.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Conception et codage du formulaire d’initiation
 Une nouvelle fonctionnalité au formulaire d’initiation en y ajoutant des contrôles et du code.  
  
#### <a name="to-code-the-initiation-form"></a>Pour coder le formulaire d’initiation  
  
1.  Dans le formulaire d’initiation (ExpenseReportInitForm.aspx), localisez le `asp:Content` élément contenant `ID="Main"`.  
  
2.  Directement après la première ligne de cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte qui affiche le plafond de dépenses (*AutoApproveLimit*) qui a été entré dans le formulaire d’association et une autre étiquette et zone de texte total des dépenses (*ExpenseTotal*) :  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Développez le **ExpenseReportInitForm.aspx** fichier **l’Explorateur de solutions** pour afficher ses fichiers dépendants.  
  
4.  Ouvrez le menu contextuel pour le fichier ExpenseReportInitForm.aspx et choisissez **afficher le Code**.  
  
5.  Remplacez le `Page_Load` méthode avec l’exemple suivant :  
  
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
  
6.  Remplacez le `GetInitiationData` méthode avec l’exemple suivant :  
  
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
  
## <a name="cutomize-the-workflow"></a>Personnaliser le flux de travail
 Ensuite, personnaliser le flux de travail. Plus tard, vous allez associer deux formulaires au flux de travail.  
  
#### <a name="to-customize-the-workflow"></a>Pour personnaliser le flux de travail  
  
1.  Afficher le flux de travail dans le Concepteur de flux de travail en ouvrant Workflow1 dans le projet.  
  
2.  Dans le **boîte à outils**, développez le **Windows Workflow v3.0** nœud et recherchez le **IfElse** activité.  
  
3.  Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :  
  
    -   Ouvrez le menu contextuel pour le **IfElse** activité, choisissez **copie**, ouvrez le menu contextuel de la ligne dans le **onWorkflowActivated1** activité dans le Concepteur de flux de travail, puis choisissez **coller**.  
  
    -   Faites glisser le **IfElse** activité à partir de la **boîte à outils**et connectez-la à la ligne sous le **onWorkflowActiviated1** activité dans le Concepteur de flux de travail.  
  
4.  Dans la boîte à outils, développez le **flux de travail SharePoint** nœud et recherchez le **CreateTask** activité.  
  
5.  Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :  
  
    -   Ouvrir le menu contextuel pour le **CreateTask** activité, choisissez **copie**, ouvrez le menu contextuel pour l’une des deux **déposer les activités ici** zones au sein de  **IfElseActivity1** dans le Concepteur de flux de travail, puis choisissez **collage**.  
  
    -   Faites glisser le **CreateTask** activité à partir de la **boîte à outils** sur l’un des deux **déposer les activités ici** domaines au sein de **IfElseActivity1**.  
  
6.  Dans le **propriétés** fenêtre, entrez une valeur de propriété *taskToken* pour le **CorrelationToken** propriété.  
  
7.  Développez le **CorrelationToken** propriété en cliquant sur le signe plus (![TreeView plu](../sharepoint/media/plus.gif "TreeView plu")) en regard de celle-ci.  
  
8.  Cliquez sur la flèche déroulante sur le **OwnerActivityName** sub de propriété, puis définissez le *Workflow1* valeur.  
  
9. Choisissez le **TaskId** propriété, puis choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) bouton pour afficher la **Lier la propriété** boîte de dialogue.  
  
10. Choisissez le **lier à un nouveau membre** , choisir le **créer un champ** case d’option, puis choisissez le **OK** bouton.  
  
11. Choisissez le **TaskProperties** propriété, puis cliquez sur le bouton de sélection (![ellipse de ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellipse de ASP.NET Mobile Designer")) pour afficher les  **Lier la propriété** boîte de dialogue.  
  
12. Choisissez le **lier à un nouveau membre** , choisir le **créer un champ** case d’option, puis choisissez le **OK** bouton.  
  
13. Dans le **boîte à outils**, développez le **flux de travail SharePoint** nœud, puis recherchez le **LogToHistoryListActivity** activité.  
  
14. Ajoutez cette activité au flux de travail en effectuant l’une des étapes suivantes :  
  
    -   Ouvrir le menu contextuel de la **LogToHistoryListActivity** activité, choisissez **copie**, ouvrir le menu contextuel pour les autres **déposer les activités ici** zone **IfElseActivity1** dans le Concepteur de flux de travail, puis choisissez **collage**.  
  
    -   Faites glisser le **LogToHistoryListActivity** activité à partir de la **boîte à outils**et déposez-le sur l’autre **déposer les activités ici** zone dans **IfElseActivity1** .  
  
## <a name="add-code-to-the-workflow"></a>Ajoutez le code au flux de travail
 Ensuite, ajoutez le code au flux de travail afin de lui donner la fonctionnalité.  
  
#### <a name="to-add-code-to-the-workflow"></a>Pour ajouter du code au flux de travail  
  
1.  Ouvrez le menu contextuel pour le **createTask1** activité dans le Concepteur de flux de travail, puis choisissez **afficher le Code**.  
  
2.  Ajoutez la méthode suivante :  
  
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
    >  Dans le code, remplacez `somedomain\\someuser` avec un nom de domaine et d’utilisateur pour lequel une tâche est créée, par exemple, «`Office\\JoeSch`». Pour le test, il est plus facile d’utiliser le compte que vous développez avec.  
  
3.  Ci-dessous le `MethodInvoking` (méthode), ajoutez l’exemple suivant :  
  
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
  
4.  Dans le Concepteur de flux de travail, choisissez la **ifElseBranchActivity1** activité.  
  
5.  Dans le **propriétés** fenêtre, cliquez sur la flèche déroulante de la **Condition** propriété, puis définissez le *Condition de Code* valeur.  
  
6.  Développez le **Condition** propriété en cliquant sur le signe plus (![TreeView plu](../sharepoint/media/plus.gif "TreeView plu")) en regard de celle-ci, puis définissez sa valeur sur *checkApprovalNeeded* .  
  
7.  Dans le Concepteur de flux de travail, ouvrez le menu contextuel pour le **logToHistoryListActivity1** activité, puis choisissez **générer les gestionnaires** pour générer une méthode vide pour le `MethodInvoking` événement.  
  
8.  Remplacez le `MethodInvoking` code par le code suivant :  
  
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
  
9. Choisissez le **F5** clé pour déboguer le programme.  
  
     Il compile l’application, empaquette, déploie, activer ses fonctionnalités, recycle le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications et puis démarre le navigateur à l’emplacement spécifié dans le **Url du Site** propriété.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Associer le flux de travail à la liste de documents
 Ensuite, afficher le formulaire d’association de flux de travail en associant le flux de travail avec le **SharedDocuments** liste sur le site SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Pour associer le flux de travail  
  
1.  Choisissez le **Documents partagés** lien dans la barre de lancement rapide.  
  
2.  Choisissez le **bibliothèque** lien sur le **outils de bibliothèque** onglet, puis choisissez le **paramètres de la bibliothèque** bouton du ruban.  
  
3.  Dans le **autorisations et gestion** , choisissez le **les paramètres de flux de travail** lier, puis choisissez le **ajouter un flux de travail** lien sur le **Workflows** page.  
  
4.  Dans la liste du haut de la page Paramètres de flux de travail, choisissez la **ExpenseReport - Workflow1** modèle.  
  
5.  Dans le champ suivant, entrez **ExpenseReportWorkflow** , puis choisissez le **suivant** bouton.  
  
     Cela associe le flux de travail avec le **Documents partagés** liste et affiche le formulaire d’association de flux de travail.  
  
6.  Dans le **limite d’approbation automatique** texte, entrez **1200** , puis choisissez le **associer le flux de travail** bouton.  
  
## <a name="start-the-workflow"></a>Démarrer le flux de travail
 Ensuite, associez le flux de travail à un des documents dans le **Documents partagés** liste pour afficher le formulaire d’initiation du flux de travail.  
  
#### <a name="to-start-the-workflow"></a>Pour démarrer le flux de travail  
  
1.  Dans la page SharePoint, choisissez le **accueil** bouton.  
  
2.  Choisissez le **Documents partagés** lien dans la barre de lancement rapide pour afficher la **Documents partagés** liste.  
  
3.  Choisissez le **Documents** lien sur le **outils de bibliothèque** onglet en haut de la page, puis choisissez le **télécharger un Document** bouton sur le ruban pour télécharger un nouveau document dans le **Documents partagés** liste.  
  
4.  Dans le **télécharger un Document** boîte de dialogue, sélectionnez le **Parcourir** bouton, choisissez n’importe quel fichier de document, le **Open** bouton, puis choisissez le **OK** bouton.  
  
     Vous pouvez modifier les paramètres pour le document dans cette boîte de dialogue, mais les conservez les valeurs par défaut en choisissant le **enregistrer** bouton.  
  
5.  Cliquez sur le document téléchargé, choisissez la flèche déroulante qui s’affiche, puis choisissez le **Workflows** élément.  
  
6.  Choisissez l’image en regard de ExpenseReportWorkflow.  
  
     Cela affiche le formulaire d’initiation du flux de travail. (Notez que la valeur affichée dans le **limite d’approbation automatique** zone est en lecture seule, car il a été entré dans le formulaire d’association.)  
  
7.  Dans le **Total des dépenses** texte, entrez **1600**, puis choisissez le **démarrer le flux de travail** bouton.  
  
     Cela permet d’afficher le **Documents partagés** liste à nouveau. Une nouvelle colonne nommée **ExpenseReportWorkflow** avec la valeur **terminé** est ajouté à l’élément de flux de travail vient de démarrer.  
  
8.  Choisissez la flèche déroulante en regard du document téléchargé, puis le **Workflows** élément pour afficher la page d’état de flux de travail. Choisissez le **terminé** valeur sous **terminé le flux de travail**. La tâche est répertoriée sous le **tâches** section.  
  
9. Cliquez sur le titre de la tâche pour afficher ses détails.  
  
10. Revenez à la **SharedDocuments** répertorier et redémarrer le flux de travail, à l’aide du même document ou une autre.  
  
11. Entrez un montant sur la page de lancement est inférieure ou égale à la quantité d’entrée dans la page de l’association (**1200**).  
  
     Lorsque cela se produit, une entrée dans la liste d’historique est créée au lieu d’une tâche. L’entrée s’affiche dans le **historique de flux de travail** section de la page d’état de flux de travail. Notez le message dans le **résultat** colonne de l’événement d’historique. Il contient le texte entré dans le `logToHistoryListActivity1.MethodInvoking` événement qui inclut le montant qui a été approuvée automatiquement.  
  
## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur la création de modèles de flux de travail à partir de ces rubriques :  
  
-   Pour en savoir plus sur les flux de travail SharePoint, consultez [des flux de travail dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Voir aussi
 [Créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Procédure pas à pas : Ajouter une page d’application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
