---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un flux de travail avec des formulaires d&#39;association et d&#39;initiation"
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
  - "formulaires d'association (développement SharePoint dans Visual Studio)"
  - "formulaires d'initiation (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, formulaires d'association de workflows"
  - "développement SharePoint dans Visual Studio, formulaires d'initiation de workflows"
  - "développement SharePoint dans Visual Studio, workflows"
  - "workflows (développement SharePoint dans Visual Studio)"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un flux de travail avec des formulaires d&#39;association et d&#39;initiation
  Cette procédure pas à pas montre comment créer un flux de travail séquentiel de base mettant en jeu des formulaires d'association et d'initiation.  Il s'agit, en l'occurrence, de formulaires ASPX permettant d'activer les paramètres à ajouter à un flux de travail lors de la première association par l'administrateur SharePoint \(formulaire d'association\) et lors du démarrage du flux de travail par l'utilisateur \(formulaire d'initiation\).  
  
 Cette procédure illustre un scénario dans lequel un utilisateur souhaite créer un flux de travail d'approbation des notes de frais présentant les caractéristiques suivantes :  
  
-   Lorsque le flux de travail est associé à une liste, un formulaire d'association est présenté à l'administrateur de façon à ce qu'il entre un seuil limite en dollars pour les notes de frais.  
  
-   Les employés téléchargent leurs notes de frais dans la liste Documents partagés, démarrent le flux de travail, puis inscrivent le montant total des dépenses dans le formulaire d'initiation de flux de travail.  
  
-   Si le montant total des dépenses reporté par un employé dépasse le seuil limite fixé par l'administrateur, une tâche est créée à l'intention du responsable de l'employé pour lui demander d'approuver la note de frais.  Toutefois, si le montant total des note de frais d'un employé est inférieur ou égal au seuil limite, un message d'auto\-approbation est consigné dans l'historique des flux de travail.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de flux de travail séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Création d'une planification de flux de travail.  
  
-   Gestion des événements d'activité de flux de travail.  
  
-   Création de formulaires d'association de flux de travail et de formulaires d'initiation de flux de travail.  
  
-   Association du flux de travail.  
  
-   Démarrage manuel du flux de travail.  
  
> [!NOTE]  
>  Bien que cette procédure pas à pas utilise un projet de flux de travail séquentiel, le processus est le même pour les flux de travail de machine à états.  
>   
>  Il est possible que pour certains des éléments de l'interface utilisateur de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Création d'un projet de flux de travail séquentiel SharePoint  
 Commencez par créer un projet de flux de travail séquentiel dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Un flux de travail séquentiel est une succession d'étapes qui s'exécutent dans l'ordre jusqu'à la fin de la dernière activité.  Au cours de cette procédure, vous allez créer un flux de travail séquentiel qui s'applique à la liste Documents partagés dans SharePoint.  L'Assistant Flux de travail permet d'une part, d'associer le flux de travail à la définition du site ou à la définition de liste et d'autre part, de déterminer à quel moment le flux de travail démarre.  
  
#### Pour créer un projet de flux de travail séquentiel SharePoint  
  
1.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
3.  Dans le volet de **Modèles**, sélectionnez le modèle de projet **Projet SharePoint 2010**.  
  
4.  Dans la zone **Nom**, entrez ExpenseReport puis cliquez sur le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
5.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.  
  
     Cette étape définit également le niveau de confiance de la solution en considérant qu'il s'agit d'une solution de la batterie, la seule option disponible pour les projets de flux de travail.  
  
6.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
7.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
8.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
9. Dans le volet **Modèles**, sélectionnez le modèle **Flux de travail séquentiel \(solution de batterie uniquement\)**, puis cliquez sur le bouton **Ajouter**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
10. Dans la page **Spécifier le nom du flux de travail pour le débogage**, acceptez le nom proposé par défaut \(**ExpenseReport \- Workflow1**\).  Conservez la valeur par défaut du type de modèle de flux de travail \(**Flux de travail de liste\)**.  Choisissez le bouton **Suivant**.  
  
11. Dans la page **Voulez\-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage**, désactivez la case qui associe automatiquement votre modèle de flux de travail.  
  
     Vous pourrez ainsi associer manuellement, par la suite, le flux de travail à la liste Documents partagés en vue d'afficher le formulaire Association.  
  
12. Choisissez le bouton **Terminer**.  
  
## Ajout d'un formulaire Association au flux de travail  
 Vous allez maintenant créer un formulaire Association .ASPX prévu pour s'afficher dès que l'administrateur SharePoint associe le flux de travail à une note de frais.  
  
#### Pour ajouter un formulaire Association au flux de travail  
  
1.  Choisissez le noeud **Workflow1** dans l'**Explorateur de solutions**.  
  
2.  Sur la barre de menu, cliquez sur **ProjetAjouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément**.  
  
3.  Dans l'arborescence de la boîte de dialogue, développez **Visual C\#** ou **Visual Basic** \(selon le langage de programmation de votre projet\), développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
4.  Dans la liste de modèles, sélectionnez le modèle **Formulaire d'association du flux de travail**.  
  
5.  Dans la zone de texte **Nom**, entrez ExpenseReportAssocForm.aspx.  
  
6.  Cliquez sur le bouton **Ajouter** pour ajouter le formulaire au projet.  
  
## Conception et codage du formulaire Association  
 L'étape suivante permet d'introduire une nouvelle fonctionnalité au formulaire Association en y incorporant des contrôles et des lignes de code.  
  
#### Pour concevoir le formulaire Association et y ajouter du code  
  
1.  Dans le formulaire d'association \(ExpenseReportAssocForm.aspx\), localisez l'élément `asp:Content` pour lequel `ID="Main"`.  
  
2.  Juste après la première ligne de cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte permettant de fixer le seuil limite des dépenses autorisées \(*AutoApproveLimit*\) :  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Développez le fichier **ExpenseReportAssocForm.aspx** dans l'**Explorateur de solutions** afin d'afficher ses fichiers dépendants.  
  
    > [!NOTE]  
    >  Si votre projet fait partie de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], vous devez cliquer sur le bouton **Afficher tous les fichiers** pour effectuer cette étape.  
  
4.  Ouvrir le menu contextuel du fichier ExpenseReportAssocForm.aspx et choisissez **Afficher le code**.  
  
5.  Remplacez la méthode `GetAssociationData` par ce qui suit :  
  
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
  
## Ajout d'un formulaire Initiation au flux de travail  
 Créez, à présent, le formulaire d'initiation affiché au moment où l'utilisateur applique le flux de travail à ses notes de frais.  
  
#### Pour créer un formulaire d'initiation  
  
1.  Choisissez le noeud **Workflow1** dans l'**Explorateur de solutions**.  
  
2.  Dans la barre de menu, cliquez sur **Projet**, **Ajouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément**.  
  
3.  Dans l'arborescence de la boîte de dialogue, développez **Visual C\#** ou **Visual Basic** \(selon le langage de programmation de votre projet\), développez le nœud **SharePoint**, puis cliquez sur le noeud**2010**.  
  
4.  Dans la liste de modèles, sélectionnez le modèle **Formulaire d'intitiation du flux de travail**.  
  
5.  Dans la zone de texte **Nom**, entrez ExpenseReportInitForm.aspx.  
  
6.  Cliquez sur le bouton **Ajouter** pour ajouter le formulaire au projet.  
  
## Conception et codage du formulaire d'initiation  
 Ajoutez une nouvelle fonctionnalité au formulaire d'initiation en y insérant des contrôles et des lignes de code.  
  
#### Pour ajouter du code au formulaire d'initiation  
  
1.  Dans le formulaire d'initiation \(ExpenseReportInitForm.aspx\), localisez l'élément `asp:Content` qui contient `ID="Main"`.  
  
2.  Juste après la première ligne de cet élément de contenu, ajoutez le code suivant pour créer une étiquette et une zone de texte permettant d'afficher le seuil limite des dépenses autorisées \(*AutoApproveLimit*\) entré dans le formulaire d'association, et prévoir une autre étiquette et une autre zone de texte correspondant au montant total des dépenses \(*ExpenseTotal*\) :  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Développez le fichier **ExpenseReportInitForm.aspx** dans l'**Explorateur de solutions** afin d'afficher ses fichiers dépendants.  
  
4.  Ouvrir le menu contextuel du fichier ExpenseReportInitForm.aspx et choisissez **Afficher le code**.  
  
5.  Remplacez la méthode `Page_Load` par l'exemple suivant :  
  
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
  
6.  Remplacez la méthode `GetInitiationData` par l'exemple suivant :  
  
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
  
## Personnalisation du flux de travail  
 Il vous appartient maintenant de personnaliser le flux de travail.  Vous aurez l'occasion, par la suite, d'associer deux formulaires au flux de travail.  
  
#### Pour personnaliser le flux de travail  
  
1.  Affichez le flux de travail dans le Concepteur de flux de travail en ouvrant Workflow1 dans le projet.  
  
2.  Dans la **Boîte à outils**, développez le nœud **Windows Workflow v3.0** et repérez l'activité **IfElse**.  
  
3.  Ajoutez cette activité au flux de travail en effectuant l'une des étapes suivantes :  
  
    -   Ouvrez le menu contextuel de l'activité **IfElse**, choisissez **Copier**, ouvrez le menu contextuel de la ligne située sous le contrôle d'activité **onWorkflowActivated** dans le concepteur de flux de travail, puis choisissez **Coller**.  
  
    -   Faites glisser l'activité **IfElse** depuis la **Boîte à outils** et connectez\-la à la ligne juste en dessous de l'activité **onWorkflowActiviated1** dans le concepteur de flux de travail.  
  
4.  Dans la Boîte à outils, développez le nœud **Flux de travail SharePoint** et repérez l'activité **CréerTâche**.  
  
5.  Ajoutez cette activité au flux de travail en effectuant l'une des étapes suivantes :  
  
    -   Ouvrez le menu contextuel de l'activité **CreateTask**, choisissez **Copier**, ouvrez le menu contextuel de l'une des deux zones **Déposer les activités ici** dans IfElseActivity1 dans le concepteur de flux de travail, puis sélectionnez **Coller**.  
  
    -   Faites glisser l'activité **CreateTask** depuis la **Boîte à outils** sur l'une des deux zones **Déposer les activités ici** dans IfElseActivity1.  
  
6.  Dans la fenêtre **Propriétés**, donnez la valeur *taskToken* à la propriété **CorrelationToken**.  
  
7.  Développez la propriété **CorrelationToken** en cliquant sur le signe plus \(![TreeView plus](~/docs/sharepoint/media/plus.gif "TreeView plus")\) en regard de celle\-ci.  
  
8.  Cliquez sur la flèche déroulante de la propriété de sous\-type **OwnerActivityName**, puis définissez la valeur *Workflow1*.  
  
9. Cliquez sur la propriété **TaskId**, puis sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/docs/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\) pour afficher la boîte de dialogue **Lier la propriété**.  
  
10. Choisissez l'onglet **Lier à un nouveau membre**, sélectionnez la case d'option **Créer un champ**, puis cliquez sur le bouton **OK**.  
  
11. Cliquez sur la propriété **TaskProperties**, puis sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/docs/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\) pour afficher la boîte de dialogue **Lier la propriété**.  
  
12. Choisissez l'onglet **Lier à un nouveau membre**, sélectionnez la case d'option **Créer un champ**, puis cliquez sur le bouton **OK**.  
  
13. Dans la **Boîte à outils**, développez le nœud **Flux de travail SharePoint** et repérez l'activité **LogToHistoryListActivity**.  
  
14. Ajoutez cette activité au flux de travail en effectuant l'une des étapes suivantes :  
  
    -   Ouvrez le menu contextuel de l'activité **LogToHistoryListActivity**, choisissez **Copier**, ouvrez le menu contextuel de l'autre zone **Déposer les activités ici** dans IfElseActivity1 dans le concepteur de flux de travail, puis sélectionnez **Coller**.  
  
    -   Faites glisser l'activité **LogToHistoryListActivity** depuis la **Boîte à outils**, et placez\-la dans l'autre zone **Déposer les activités ici** dans IfElseActivity1.  
  
## Ajout du code au flux de travail  
 Veuillez maintenant ajouter le code au flux de travail pour le rendre fonctionnel.  
  
#### Pour ajouter du code au flux de travail  
  
1.  Ouvrir le menu contextuel de l'activité **createTask1** dans le concepteur de flux de travail, puis sélectionnez **Afficher le code**.  
  
2.  Ajoutez la méthode  suivante :  
  
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
    >  Dans le code, remplacez `somedomain\\someuser` par un nom de domaine et un nom d'utilisateur pour lesquels vous comptez créer une tâche \(`Office\\JoeSch`, par exemple\).  Pour mener à bien le test, il est plus simple d'utiliser le compte de développement.  
  
3.  Ajoutez l'exemple suivant sous la méthode `MethodInvoking` :  
  
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
  
4.  Dans le Concepteur de flux de travail, cliquez sur l'activité **ifElseBranchActivity1**.  
  
5.  Dans la fenêtre **Propriétés**, cliquez sur la flèche déroulante de la propriété **Condition**, puis mettez la valeur *Code Condition*.  
  
6.  Développez la propriété **Condition** en cliquant sur le signe plus \(![TreeView plus](~/docs/sharepoint/media/plus.gif "TreeView plus")\) en regard de celle\-ci, puis donnez\-lui la valeur *checkApprovalNeeded*.  
  
7.  Dans le Concepteur de flux de travail, ouvrez le menu contextuel de l'activité **logToHistoryListActivity1**, puis sélectionnez **Générer les gestionnaires** afin de créer une méthode vide pour l'événement `MethodInvoking`.  
  
8.  Remplacez le code `MethodInvoking` par ce qui suit :  
  
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
  
9. Appuyez sur la touche F5 pour debugger le programme.  
  
     Cela a pour effet de compiler l'application, de l'empaqueter, de la déployer, d'activer ses fonctionnalités, de recycler le pool d'applications [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)], puis de démarrer le navigateur à l'emplacement spécifié dans la propriété **URL du site**.  
  
## Association du flux de travail à la liste de documents  
 Il convient, à présent, d'affichez le formulaire d'association de flux de travail en associant le flux de travail à la liste **Documentspartagés** sur le site SharePoint.  
  
#### Pour associer le flux de travail  
  
1.  Cliquez sur le lien **Documents partagés** dans la barre de lancement rapide.  
  
2.  Cliquez sur le lien **Bibliothèque** dans l'onglet **Outils de bibliothèque**, puis sur le bouton de ruban **Paramètres de la bibliothèque**.  
  
3.  Dans la section **Autorisations et gestion**, cliquez sur le lien **Paramètres du flux de travail**, puis sur le lien **Ajouter un flux de travail** à la page **Flux de travail**.  
  
4.  Dans la liste figurant en haut de la page des paramètres de flux de travail, sélectionnez le modèle **ExpenseReport \- Workflow1**.  
  
5.  Dans le champ suivant, entrez ExpenseReportWorkflow, puis cliquez sur le bouton **Suivant**.  
  
     Cela permet d'associer le flux de travail à la liste **Documents partagés** et d'afficher le formulaire d'association de flux de travail.  
  
6.  Dans la zone de texte **Limite d'approbation automatique**, entrez 1200, puis cliquez sur le bouton **Associer le flux de travail**.  
  
## Démarrage du flux de travail  
 Associez ensuite le flux de travail à l'un des documents de la liste **Documents partagés** pour afficher le formulaire d'initiation de flux de travail.  
  
#### Pour démarrer le flux de travail  
  
1.  Sur la page SharePoint, choisissez le bouton **Accueil**.  
  
2.  Sélectionnez le lien **Documents partagés** dans la barre de lancement rapide pour afficher la liste des **Documents partagés**.  
  
3.  Cliquez sur le lien **Documents** de l'onglet **Outils de bibliothèques** en haut de la page, puis cliquez sur**Télécharger le document** sur le ruban pour télécharger un nouveau document dans la liste de **Documents partagés**.  
  
4.  Dans la boîte de dialogue **Télécharger des documents**, cliquez sur le bouton **Parcourir**, choisissez un fichier document, cliquez sur le bouton **Ouvrir**, puis cliquez sur le bouton **OK**.  
  
     Vous pouvez modifier les paramètres relatifs au document dans cette boîte de dialogue mais veuillez conserver les valeurs par défaut en cliquant sur le bouton **Enregistrer**.  
  
5.  Choisissez le document téléchargé, cliquez sur la flèche déroulante qui s'affiche, puis choisissez l'élément **Flux de travail**.  
  
6.  Cliquez sur l'image à côté de ExpenseReportWorkflow.  
  
     Cela a pour effet d'afficher le formulaire d'initiation du flux de travail. Notez que la valeur affichée dans la zone **Limite d'approbation automatique** est en lecture seule, car elle a été entrée dans le formulaire d'association.  
  
7.  Dans la zone de texte **Frais totaux**, tapez 1600, puis cliquez sur le bouton **Démarrer le flux de travail**.  
  
     Vous accédez à nouveau à la liste **Documents partagés**.  Une nouvelle colonne appelée **ExpenseReportWorkflow** contenant la valeur **Terminé** est ajoutée à l'élément venant juste d'être démarré par le flux de travail.  
  
8.  Cliquez sur la flèche déroulante en regard du document téléchargé, puis cliquez sur l'élément **Flux de travail** pour afficher la page État du flux de travail.  Cliquez sur la valeur **Terminé** en dessous de **Flux de travail terminés**.  La tâche est répertoriée dans la section **Tâches**.  
  
9. Cliquez sur le titre de la tâche pour afficher ses détails.  
  
10. Revenez à la liste **Documents partagés** et redémarrez le flux de travail en utilisant le même document ou un autre document.  
  
11. Entrez, dans le formulaire d'initiation, un montant inférieur ou égal au montant entré dans le formulaire d'association \(1200\).  
  
     Cela donne lieu à une entrée \(et non une tâche\) dans l'historique.  L'entrée apparaît dans la section **Historique des flux de travail** de la page État du flux de travail.  Notez le message dans la colonne **Résultat** de l'événement d'historique.  Il contient le texte entré dans l'événement `logToHistoryListActivity1.MethodInvoking` où est inscrit le montant auto\-approuvé.  
  
## Étapes suivantes  
 Pour plus d'informations sur la création de modèles de flux de travail, consultez les rubriques suivantes :  
  
-   Pour en savoir plus sur les flux de travail SharePoint, consultez [Flux de travail dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## Voir aussi  
 [Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Procédure pas à pas : ajout d'une page d'application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  