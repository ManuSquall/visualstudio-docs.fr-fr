---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation et d&#233;bogage d&#39;une solution de flux de travail SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, workflows"
  - "workflows (développement SharePoint dans Visual Studio)"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation et d&#233;bogage d&#39;une solution de flux de travail SharePoint
  Cette procédure pas à pas montre comment créer un modèle de flux de travail séquentiel de base.  Le flux de travail vérifie une propriété d'une bibliothèque de documents partagés afin de déterminer si un document a été révisé.  Si le document a été révisé, le flux de travail se termine.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de flux de travail séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Création d'activités de flux de travail.  
  
-   Gestion des événements d'activité de flux de travail.  
  
> [!NOTE]  
>  Bien que cette procédure fasse appel à un projet de flux de travail séquentiel, le processus est identique pour un projet de flux de travail de machine à états.  
>   
>  Il est possible, en outre, que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Ajout de propriétés à la bibliothèque Documents partagés du site SharePoint  
 Pour suivre l'état de la révision des documents dans la bibliothèque **Documents partagés**, il convient de définir trois nouvelles propriétés pour les documents partagés sur notre site SharePoint : `Status`, `Assignee` et `Review Comments`.  Nous allons, pour ce faire, ajouter ces propriétés à la bibliothèque **Documents partagés**.  
  
#### Pour ajouter des propriétés à la bibliothèque Documents partagés du site SharePoint  
  
1.  Ouvrez un site SharePoint, comme par exemple http:\/\/\<nom du système\>\/SitePages\/Home.aspx, dans un navigateur Web.  
  
2.  Cliquez sur **Documents partagés** dans la barre de lancement rapide.  
  
3.  Cliquez sur **Bibliothèque** sur le ruban **Outils de bibliothèque**, puis sur le bouton **Créer une colonne** sur le ruban pour définir une nouvelle colonne.  
  
4.  Nommez la colonne État du document, choisissez le type **Choix \(menu dans lequel effectuer un choix\)**, spécifiez les trois choix suivants, puis cliquez sur le bouton **OK** :  
  
    -   **Révision nécessaire**  
  
    -   **Révision terminée**  
  
    -   **Modifications demandées**  
  
5.  Créez deux colonnes supplémentaires et nommez\-les Cessionnaire et Commentaires de révision.  Mettez en forme la colonne Cessionnaire comme une ligne unique de texte, et la colonne Commentaires de révision comme lignes de texte multiples.  
  
## Modification de documents sans extraction  
 Le test du modèle de flux de travail est plus facile lorsque vous pouvez modifier les documents sans devoir les extraire.  Vous allez à présent configurer le site SharePoint à cet effet.  
  
#### Pour modifier des documents sans les extraire  
  
1.  Cliquez sur le lien **Documents partagés** dans la barre de lancement rapide.  
  
2.  Dans le ruban **Outils de bibliothèque** cliquez sur **Bibliothèque** puis sur le bouton **Paramètres de la bibliothèque** pour afficher la page **Paramètres de la bibliothèque de documents**.  
  
3.  Dans la section **Paramètres généraux**, cliquez sur le lien **Paramètres de contrôle de version** pour afficher la page **Paramètres de contrôle de version**.  
  
4.  Vérifiez que la valeur du paramètre **Exiger l'extraction des documents avant de pouvoir les modifier** est **Non**.  Dans le cas contraire, sélectionnez la valeur **Non**, puis cliquez sur le bouton **OK**.  
  
5.  Fermez le navigateur.  
  
## Création d'un projet de flux de travail séquentiel SharePoint  
 Un flux de travail séquentiel est une succession d'étapes qui s'exécutent dans l'ordre jusqu'à la fin de la dernière activité.  Vous allez maintenant créer un flux de travail séquentiel qui s'appliquera à notre liste Documents partagés.  L'Assistant Flux de travail permet d'une part, d'associer le flux de travail à la définition du site ou à la définition de liste et d'autre part, de déterminer à quel moment le flux de travail démarre.  
  
#### Pour créer un projet de flux de travail séquentiel SharePoint  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
3.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
4.  Dans le volet de **Modèles**, sélectionnez le modèle **Projet SharePoint 2010**.  
  
5.  Dans la zone de texte **Nom**, entrez MySharePointWorkflow, puis choisissez le bouton OK.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
6.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.  
  
     Cette étape définit le niveau de confiance de la solution en considérant qu'il s'agit d'une solution de la batterie, la seule option disponible pour les projets de flux de travail.  Pour plus d'informations, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Dans l'**Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **Project**, **Ajouter un nouvel objet**.  
  
8.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
9. Dans le volet **Modèles**, sélectionnez le modèle **Flux de travail séquentiel \(solution de batterie uniquement\)**, puis cliquez sur le bouton **Ajouter**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
10. Dans la page **Spécifier le nom du flux de travail pour le débogage**, acceptez le nom proposé par défaut \(**MonFluxdetravailSharePoint \- Workflow1**\).  Conservez la valeur du type de modèle de flux de travail par défaut, **Flux de travail de liste**, puis cliquez sur le bouton **Suivant**.  
  
11. Dans la page **Voulez\-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage**, cliquez sur le bouton **Suivant** pour accepter tous les paramètres par défaut.  
  
     Cette étape associe automatiquement le flux de travail à la bibliothèque Documents partagés.  
  
12. Dans la page **Spécifier les conditions de démarrage du flux de travail**, conservez les options par défaut qui sont sélectionnées dans la section **Comment le flux de travail doit\-il commencer ?**, puis cliquez sur le bouton **Terminer**.  
  
     Cette page vous permet de spécifier le moment où votre flux de travail démarre.  Par défaut, le flux de travail démarre lorsqu'il est lancé manuellement par un utilisateur dans SharePoint ou lorsqu'un élément auquel le flux de travail est associé est créé.  
  
## Création d'activités de flux de travail  
 Les flux de travail contiennent une ou plusieurs *activités* représentant les actions à effectuer.  Servez\-vous du Concepteur de flux de travail pour organiser les activités au sein d'un flux de travail.  Dans cette procédure, nous allons ajouter deux activités au flux de travail : HandleExternalEventActivity et OnWorkFlowItemChanged.  Ces activités permettent de surveiller l'état de la révision des documents dans la liste **Documents partagés**.  
  
#### Pour créer des activités de flux de travail  
  
1.  Le flux de travail doit s'afficher dans le Concepteur de flux de travail.  Dans le cas contraire, ouvrez soit **Workflow1.cs** soit **Workflow1.vb** dans l'**Explorateur de solutions**.  
  
2.  Dans le concepteur, cliquez sur l'activité **OnWorkflowActivated1**.  
  
3.  Dans la fenêtre **Propriétés**, tapez onWorkflowActivated en regard de la propriété **Invoked**, puis appuyez sur la touche Entrer.  
  
     L'éditeur de code ouvre et une méthode de gestionnaire d'événements nommée onWorkflowActivated est ajoutée au fichier de code Workflow1.  
  
4.  Revenez au Concepteur de flux de travail, ouvrez la boîte à outils, puis développez le nœud **Windows Workflow v3.0**.  
  
5.  Dans le nœud **Windows v3.0 travail** de la **Boîte à outils**, effectuez l'une des étapes suivantes.  
  
    1.  Ouvrez le menu contextuel de l'activité **Pendant**, puis choisissez **Copier**.  Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne dans l'activité **onWorkflowActivated1**, puis choisissez **Coller**.  
  
    2.  Faites glisser l'activité **While** depuis la **Boîte à outils** vers le concepteur de flux de travail, et connectez l'activité à la ligne juste en dessous de l'activité **onWorkflowActivated1**.  
  
6.  Sélectionnez l'activité **WhileActivity1**.  
  
7.  Dans la fenêtre **Propriétés**, affectez la valeur Condition de code à **Condition**.  
  
8.  Développez la propriété **Condition**, tapez isWorkflowPending en regard de la propriété enfant **Condition**, puis appuyez la touche Entrer.  
  
     L'éditeur de code s'ouvre et une méthode nommée isWorkflowPending est ajoutée au fichier de code Workflow1.  
  
9. Revenez au Concepteur de flux de travail, ouvrez la boîte à outils, puis développez le nœud **Flux de travail SharePoint**.  
  
10. Dans le nœud **Sharepoint Workflow** de la **Boîte à outils**, effectuez l'une des étapes suivantes.  
  
    -   Ouvrez le menu contextuel de l'activité **OnWorkflowItemChanged**, puis choisissez **Copier**.  Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne dans l'activité **whileActivity1**, puis choisissez **Coller**.  
  
    -   Faites glisser l'activité **OnWorkflowItemChanged** depuis la**Boîte à outils** vers le concepteur de flux de travail et connectez l'activité à la ligne à l'intérieur de l'activité **whileActivity1**.  
  
11. Sélectionnez l'activité **onWorkflowItemChanged1**.  
  
12. Dans la fenêtre **Propriétés**, définissez les propriétés affichées dans le tableau suivant.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## Gestion d'événements d'activité  
 Pour finir, vérifiez l'état du document à partir de chaque activité.  Si le document a été révisé, le flux de travail se termine.  
  
#### Pour gérer des événements d'activité  
  
1.  Dans Workflow1.cs ou Workflow1.vb, ajoutez le champ suivant en haut de la classe `Workflow1`.  Vous utilisez ce champ dans une activité pour déterminer si le flux de travail est terminé.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Ajoutez la méthode suivante à la classe `Workflow1`.  Cette méthode vérifie la valeur de la propriété `Document Status` de la liste Documents pour déterminer si le document a été révisé.  Si la propriété `Document Status` a la valeur `Review Complete`, la méthode `checkStatus` affecte au champ `workflowPending` la valeur **false** pour indiquer que le flux de travail est prêt à se terminer.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Ajoutez le code suivant aux méthodes `onWorkflowActivated` et `onWorkflowItemChanged` pour appeler la méthode `checkStatus`.  Lorsque le flux de travail démarre, la méthode `onWorkflowActivated` appelle la méthode `checkStatus` pour déterminer si le document a déjà été révisé.  S'il n'a pas été révisé, le flux de travail continue.  Lorsque le document est enregistré, la méthode `onWorkflowItemChanged` appelle de nouveau la méthode `checkStatus` pour déterminer si le document a été révisé.  Tant que le champ `workflowPending` a la valeur **true**, le flux de travail continue à s'exécuter.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Ajoutez le code suivant à la méthode `isWorkflowPending` pour vérifier l'état de la propriété `workflowPending`.  Chaque fois que le document est enregistré l'activité **whileActivity1** appelle la méthode `isWorkflowPending`.  Cette méthode examine la propriété <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> de l'objet <xref:System.Workflow.Activities.ConditionalEventArgs> pour déterminer si l'activité **WhileActivity1** doit continuer ou se terminer.  Si la propriété a la valeur **true**, l'activité continue.  Sinon, l'activité se termine, ainsi que le flux de travail.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Enregistrez le projet.  
  
## Test du modèle de flux de travail SharePoint  
 Lorsque vous démarrez le débogueur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie le modèle de flux de travail vers le serveur SharePoint et associe le flux de travail à la liste **Documents partagés**.  Pour tester le flux de travail, démarrez une instance du flux de travail à partir d'un document de la liste **Documents partagés**.  
  
#### Pour tester le modèle de flux de travail SharePoint  
  
1.  Dans Workflow1.cs ou Workflow1.vb, définissez un point d'arrêt en regard de méthode **onWorkflowActivated**.  
  
2.  Appuyez sur la touche F5 pour générer et exécuter la solution.  
  
     Le site SharePoint s'affiche.  
  
3.  Dans le volet de navigation de SharePoint, cliquez sur le lien **Documents** partagés.  
  
4.  Dans la page **Documents partagés**, cliquez sur **Documents** sous l'onglet **Outils de bibliothèque**, puis sur le bouton **Téléchargement un document**.  
  
5.  Dans la boîte de dialogue **Télécharger des documents**, cliquez sur le bouton **Parcourir**, choisissez un fichier document, cliquez sur le bouton **Ouvrir**, puis cliquez sur le bouton **OK**.  
  
     Cela a pour effet de télécharger le document sélectionné dans la liste **Documents partagés** et de démarrer le flux de travail.  
  
6.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vérifiez que le débogueur s'arrête au point d'arrêt en regard de la méthode `onWorkflowActivated`.  
  
7.  Appuyez sur la touche F5 pour continuer l'exécution.  
  
8.  Vous pouvez modifier les paramètres relatifs au document à cet endroit. Pour l'instant, veuillez conserver les valeurs par défaut en cliquant sur le bouton **Enregistrer**.  
  
     Vous revenez alors à la page **Documents partagés** du site Web SharePoint par défaut.  
  
9. Sur la page **Documents partagés**, vérifiez que la valeur en dessous de la colonne **MySharePointWorkflow – Workflow1** est bien **en progrès**.  Cela signifie que le flux de travail est en cours de réalisation et que le document attend d'être révisé.  
  
10. Dans la page **Documents partagés**, choisissez le document, choisissez la flèche qui s'affiche, puis cliquez sur l'élément de menu **Modifier les propriétés**.  
  
11. Affectez à **État du document** la valeur **Révision terminée**, puis cliquez sur le bouton **Enregistrer**.  
  
     Vous revenez alors à la page **Documents partagés** du site Web SharePoint par défaut.  
  
12. À la page **Documents partagés**, assurez\-vous que la valeur sous la colonne **Statut du document** correspond à **Révision terminée**.  Actualisez la page **Documents partagés** et assurez\-vous que la valeur sous la colonne **MonFluxdetravailSharePoint – Workflow1** correspond à **Révision terminée**.  Cela signifie que le flux de travail est terminé et que le document a été révisé.  
  
## Étapes suivantes  
 Pour plus d'informations sur la création de modèles de flux de travail, consultez les rubriques suivantes :  
  
-   Pour plus d'informations sur les activités de flux de travail SharePoint, consultez [Activités de flux de travail pour SharePoint Foundation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Pour plus d'informations sur les activités Windows Workflow Foundation, consultez [System.Workflow.Activities, espace de noms](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## Voir aussi  
 [Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  