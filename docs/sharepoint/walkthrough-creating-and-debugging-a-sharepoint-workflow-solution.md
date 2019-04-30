---
title: 'Procédure pas à pas : Création et débogage d’une Solution de flux de travail SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad39c8b8bad373cd7892a1eeda89b149622913a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430367"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Procédure pas à pas : Créer et déboguer une solution de flux de travail SharePoint
  Cette procédure pas à pas montre comment créer un modèle de workflow séquentiel de base. Le flux de travail vérifie une propriété d’une bibliothèque de documents partagés pour déterminer si un document a été révisé. Si le document a été révisé, le flux de travail se termine.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de workflow séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Création d’activités de flux de travail.

- Gestion des événements d’activité de flux de travail.

> [!NOTE]
> Bien que cette procédure pas à pas utilise un projet de workflow séquentiel, le processus est identique pour un projet de flux de travail de machine état.
>
> En outre, votre ordinateur peut afficher des noms différents ou emplacements de l’utilisateur de Visual Studio pour les éléments d’interface dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Ajouter des propriétés à la bibliothèque de documents partagés SharePoint
 Pour suivre l’état de révision de documents dans le **Documents partagés** bibliothèque, nous allons créer trois nouvelles propriétés pour les documents partagés sur notre site SharePoint : `Status`, `Assignee`, et `Review Comments`. Nous définissons ces propriétés dans le **Documents partagés** bibliothèque.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Pour ajouter des propriétés à SharePoint partagé bibliothèque de documents

1. Ouvrir un site SharePoint, par exemple http://\<nom système > / SitePages, dans un navigateur Web.

2. Dans la barre de lancement rapide, choisissez **SharedDocuments**.

3. Choisissez **bibliothèque** sur le **outils de bibliothèque** ruban, puis choisissez le **créer une colonne** bouton sur le ruban pour créer une nouvelle colonne.

4. Nom de la colonne **Document état**, définissez son type sur **choix (menu sélectionnables)**, spécifiez les trois choix suivants, puis choisissez le **OK** bouton :

    - **Révision nécessaire**

    - **Révision terminée**

    - **Modifications demandées**

5. Création de deux colonnes supplémentaires et nommez-les **intervenant** et **les commentaires de révision**. Définissez le type de colonne de personne responsable en tant qu’une seule ligne de texte et le type de colonne de commentaires de révision en tant que plusieurs lignes de texte.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Activer la modification sans nécessiter une extraction de documents
 Il est plus facile de tester le modèle de flux de travail lorsque vous pouvez modifier les documents sans avoir à les extraire. Dans la procédure suivante, vous configurez le site SharePoint pour cela.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Pour activer la modification sans leur extraction de documents

1. Dans la barre de lancement rapide, choisissez le **Documents partagés** lien.

2. Sur le **outils de bibliothèque** ruban, choisissez le **bibliothèque** onglet, puis choisissez le **paramètres de la bibliothèque** bouton pour afficher le **Document Library Settings** page.

3. Dans le **paramètres généraux** , choisissez le **les paramètres de contrôle de version** lien pour afficher le **les paramètres de contrôle de version** page.

4. Vérifiez que le paramètre pour **exiger que les documents à extraire avant de pouvoir modifier** est **non**. Si elle n’est pas le cas, remplacez-le par **non** , puis choisissez le **OK** bouton.

5. Fermez le navigateur.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Créer un projet de flux de travail séquentiel SharePoint
 Un workflow séquentiel est un ensemble d’étapes qui s’exécute dans l’ordre jusqu'à la fin de la dernière activité. Dans cette procédure, nous créer un workflow séquentiel qui s’appliqueront à notre liste de Documents partagés. L’Assistant flux de travail vous permet d’associer le flux de travail avec la définition de site ou la définition de liste et vous permet de déterminer quand le flux de travail démarre.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Pour créer un projet de flux de travail séquentiel SharePoint

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.

3. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

4. Dans le **modèles** volet, choisissez le **projet SharePoint 2010** modèle.

5. Dans le **nom** , entrez **MonFluxdetravailSharePoint** , puis choisissez le **OK** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

6. Dans le **spécifier le niveau de site et de sécurité pour le débogage** page, choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton pour accepter le site par défaut et le niveau de confiance.

     Cette étape définit le niveau de confiance pour la solution en tant que solution de batterie de serveurs, la seule option disponible pour les projets de flux de travail. Pour plus d’informations, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).

7. Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément**.

8. Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

9. Dans le **modèles** volet, choisissez le **Workflow séquentiel (Solution de batterie uniquement)** modèle, puis choisissez le **ajouter** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

10. Dans le **spécifier le nom de flux de travail pour le débogage** page, acceptez le nom par défaut (**MonFluxdetravailSharePoint - Workflow1**). Conserver la valeur par défaut du type de modèle de flux de travail, **flux de travail de liste**, puis choisissez le **suivant** bouton.

11. Dans le **voulez-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage ?** page, choisissez le **suivant** bouton pour accepter tous les paramètres par défaut.

     Cette étape associe automatiquement le flux de travail à la bibliothèque Documents partagés.

12. Dans le **spécifier les conditions de votre flux de travail démarrage** page, conservez les sélections par défaut dans le **Comment voulez-vous que le flux de travail pour démarrer ?** section et choisissez le **Terminer** bouton.

     Cette page vous permet de spécifier au démarrage du workflow. Par défaut, le flux de travail démarre lorsqu’un utilisateur démarre manuellement dans SharePoint ou lorsqu’un élément auquel le flux de travail est associé est créé.

## <a name="create-workflow-activities"></a>Créer des activités de flux de travail
 Flux de travail contiennent un ou plusieurs *activités* qui représentent des actions à effectuer. Utilisez le Concepteur de flux de travail pour organiser des activités pour un flux de travail. Dans cette procédure, nous allons ajouter deux activités au flux de travail : HandleExternalEventActivity et OnWorkFlowItemChanged. Ces activités permettent de surveiller l’état de révision de documents dans le **Documents partagés** liste

#### <a name="to-create-workflow-activities"></a>Pour créer des activités de flux de travail

1. Le flux de travail doit s’afficher dans le Concepteur de flux de travail. Si elle n’est pas le cas, puis ouvrez soit **Workflow1.cs** ou **Workflow1.vb** dans **l’Explorateur de solutions**.

2. Dans le concepteur, choisissez le **OnWorkflowActivated1** activité.

3. Dans le **propriétés** fenêtre, entrez **onWorkflowActivated** à côté du **Invoked** propriété, puis choisissez la touche ENTRÉE.

     L’éditeur de Code s’ouvre, et une méthode de gestionnaire d’événements nommée onWorkflowActivated est ajoutée au fichier de code Workflow1.

4. Revenez au Concepteur de flux de travail, ouvrez la boîte à outils et puis développez le **Windows Workflow v3.0** nœud.

5. Dans le **Windows Workflow v3.0** nœud de la **boîte à outils**, effectuez l’une des ensembles d’étapes suivants :

    1. Ouvrez le menu contextuel pour le **tandis que** activité, puis choisissez **copie**. Dans le Concepteur de flux de travail, ouvrez le menu contextuel de la ligne sous le **onWorkflowActivated1** activité, puis choisissez **coller**.

    2. Faites glisser le **tandis que** activité à partir de la **boîte à outils** vers le Concepteur de flux de travail et connectez l’activité à la ligne sous le **onWorkflowActivated1** activité.

6. Choisissez le **WhileActivity1** activité.

7. Dans le **propriétés** fenêtre, définissez **Condition** à Condition de Code.

8. Développez le **Condition** propriété, entrez **isWorkflowPending** en regard de l’enfant **Condition** propriété, puis choisissez la touche ENTRÉE.

     L’éditeur de Code s’ouvre, et une méthode nommée isWorkflowPending est ajoutée au fichier de code Workflow1.

9. Revenez au Concepteur de flux de travail, ouvrez la boîte à outils et puis développez le **flux de travail SharePoint** nœud.

10. Dans le **flux de travail SharePoint** nœud de la **boîte à outils**, effectuez l’une des ensembles d’étapes suivants :

    - Ouvrez le menu contextuel pour le **OnWorkflowItemChanged** activité, puis choisissez **copie**. Dans le Concepteur de flux de travail, ouvrez le menu contextuel de la ligne à l’intérieur de la **whileActivity1** activité, puis choisissez **coller**.

    - Faites glisser le **OnWorkflowItemChanged** activité à partir de la **boîte à outils** vers le Concepteur de flux de travail et connectez l’activité à la ligne à l’intérieur de la **whileActivity1** activité.

11. Choisissez le **onWorkflowItemChanged1** activité.

12. Dans le **propriétés** fenêtre, définissez les propriétés comme indiqué dans le tableau suivant.

    |Propriété|Value|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Appelée**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Gérer les événements d’activité
 Enfin, vérifiez l’état du document à partir de chaque activité. Si le document a été révisé, le flux de travail est terminé.

#### <a name="to-handle-activity-events"></a>Pour gérer les événements d’activité

1. Dans *Workflow1.cs* ou *Workflow1.vb*, ajoutez le champ suivant en haut de la `Workflow1` classe. Ce champ est utilisé dans une activité pour déterminer si le flux de travail est terminé.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Ajoutez la méthode suivante à la classe `Workflow1` . Cette méthode vérifie la valeur de la `Document Status` propriété de la liste de Documents pour déterminer si le document a été révisé. Si le `Document Status` propriété est définie sur `Review Complete`, puis le `checkStatus` méthode indique le `workflowPending` champ **false** pour indiquer que le flux de travail est prêt à terminer.

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

3. Ajoutez le code suivant à la `onWorkflowActivated` et `onWorkflowItemChanged` méthodes à appeler le `checkStatus` (méthode). Lorsque le workflow démarre, le `onWorkflowActivated` les appels de méthode le `checkStatus` méthode pour déterminer si le document a déjà été révisé. Si elle n’a pas été révisé, le flux de travail continue. Lorsque le document est enregistré, le `onWorkflowItemChanged` les appels de méthode le `checkStatus` méthode pour déterminer si le document a été révisé. Bien que le `workflowPending` champ est défini sur **true**, le flux de travail continue à s’exécuter.

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

4. Ajoutez le code suivant à la `isWorkflowPending` méthode pour vérifier l’état de la `workflowPending` propriété. Chaque fois que le document est enregistré, le **whileActivity1** activité appelle le `isWorkflowPending` (méthode). Cette méthode examine la <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> propriété de la <xref:System.Workflow.Activities.ConditionalEventArgs> objet pour déterminer si le **WhileActivity1** activité doit continuer ou se terminer. Si la propriété est définie sur **true**, l’activité continue. Sinon, l’activité se termine et le flux de travail se termine.

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

5. Enregistrez le projet.

## <a name="test-the-sharepoint-workflow-template"></a>Testez le modèle de flux de travail SharePoint
 Lorsque vous démarrez le débogueur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie le modèle de flux de travail vers le serveur SharePoint et associe le flux de travail avec le **Documents partagés** liste. Pour tester le flux de travail, démarrez une instance du flux de travail à partir d’un document dans le **Documents partagés** liste.

#### <a name="to-test-the-sharepoint-workflow-template"></a>Pour tester le modèle de flux de travail SharePoint

1. Dans *Workflow1.cs* ou *Workflow1.vb*, définissez un point d’arrêt à côté du **onWorkflowActivated** (méthode).

2. Choisissez le **F5** clé pour générer et exécuter la solution.

     Le site SharePoint s’affiche.

3. Dans le volet de navigation dans SharePoint, choisissez le **Documents partagés** lien.

4. Dans le **Documents partagés** page, choisissez le **Documents** lien sur le **outils de bibliothèque** onglet, puis choisissez le **télécharger un Document** bouton .

5. Dans le **télécharger un Document** boîte de dialogue, sélectionnez le **Parcourir** bouton, choisissez n’importe quel fichier de document, le **Open** bouton, puis choisissez le **OK** bouton.

     Cela télécharge le document sélectionné dans le **Documents partagés** répertorier et démarre le workflow.

6. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vérifiez que le débogueur s’arrête au point d’arrêt à côté du `onWorkflowActivated` (méthode).

7. Choisissez le **F5** touche pour continuer l’exécution.

8. Vous pouvez modifier les paramètres pour le document ici, mais conservez les valeurs par défaut pour l’instant en choisissant le **enregistrer** bouton.

     Cela vous ramène à la **Documents partagés** page du site Web SharePoint par défaut.

9. Dans le **Documents partagés** page, vérifiez que la valeur en dessous de la **MonFluxdetravailSharePoint - Workflow1** colonne est définie sur **en cours**. Cela indique que le flux de travail est en cours d’exécution et que le document est en attente de révision.

10. Dans le **Documents partagés** page, choisissez le document, cliquez sur la flèche qui apparaît, puis choisissez le **modifier les propriétés** élément de menu.

11. Définissez **état du Document** à **révision terminée**, puis choisissez le **enregistrer** bouton.

     Cela vous ramène à la **Documents partagés** page du site Web SharePoint par défaut.

12. Dans le **Documents partagés** page, vérifiez que la valeur en dessous de la **Document état** colonne est définie sur **révision terminée**. Actualiser le **Documents partagés** page et vérifiez que la valeur en dessous de la **MonFluxdetravailSharePoint - Workflow1** colonne est définie sur **terminé**. Cela indique que flux de travail est terminé et que le document a été révisé.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur la création de modèles de flux de travail à partir de ces rubriques :

- Pour en savoir plus sur les activités de flux de travail SharePoint, consultez [des activités de flux de travail pour SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).

- Pour en savoir plus sur les activités Windows Workflow Foundation, consultez [sous Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).

## <a name="see-also"></a>Voir aussi
- [Créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
