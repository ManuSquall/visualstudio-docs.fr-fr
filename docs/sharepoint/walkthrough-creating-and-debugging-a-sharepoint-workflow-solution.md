---
title: Créer & déboguer une solution de flux de travail SharePoint
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
ms.openlocfilehash: 0e62226147fc160c6d967115fbd3aaa52dd69995
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985062"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Procédure pas à pas : créer et déboguer une solution de flux de travail SharePoint
  Cette procédure pas à pas montre comment créer un modèle de flux de travail séquentiel de base. Le flux de travail vérifie une propriété d’une bibliothèque de documents partagée pour déterminer si un document a été révisé. Si le document a été révisé, le flux de travail se termine.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de flux de travail séquentiel de définition de liste SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Création d’activités de flux de travail.

- Gestion des événements d’activité de flux de travail.

> [!NOTE]
> Bien que cette procédure pas à pas utilise un projet de workflow séquentiel, le processus est identique pour un projet de workflow d’ordinateur d’État.
>
> En outre, il se peut que votre ordinateur affiche des noms ou des emplacements différents pour certains éléments de l’interface utilisateur de Visual Studio dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Ajouter des propriétés à la bibliothèque de documents partagés SharePoint
 Pour suivre l’état de la révision des documents dans la bibliothèque **documents partagés** , nous allons créer trois nouvelles propriétés pour les documents partagés sur notre site SharePoint : `Status`, `Assignee`et `Review Comments`. Nous définissons ces propriétés dans la bibliothèque **documents partagés** .

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Pour ajouter des propriétés à la bibliothèque de documents partagés SharePoint

1. Ouvrez un site SharePoint, par exemple http://\<nom du système >/SitePages/Home.aspx, dans un navigateur Web.

2. Dans la barre de lancement rapide, choisissez **SharedDocuments**.

3. Choisissez **bibliothèque** dans le ruban **outils de bibliothèque** , puis cliquez sur le bouton créer une **colonne** sur le ruban pour créer une colonne.

4. Nommez la colonne **État du document**, définissez son type sur **Choice (menu à sélectionner)** , spécifiez les trois options suivantes, puis choisissez le bouton **OK** :

    - **Examen nécessaire**

    - **Révision terminée**

    - **Modifications demandées**

5. Créez deux colonnes supplémentaires et nommez-les **assigner** et **passez en revue les commentaires**. Définissez le type de colonne Assigned comme une seule ligne de texte et le type de colonne commentaires de révision sur plusieurs lignes de texte.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Autoriser la modification des documents sans avoir à extraire
 Il est plus facile de tester le modèle de flux de travail lorsque vous pouvez modifier les documents sans avoir à les extraire. Dans la procédure suivante, vous configurez le site SharePoint pour l’activer.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Pour permettre la modification des documents sans les extraire

1. Dans la barre de lancement rapide, choisissez le lien **documents partagés** .

2. Dans le ruban **outils de bibliothèque** , choisissez l’onglet **bibliothèque** , puis cliquez sur le bouton Paramètres de la **bibliothèque** pour afficher la page Paramètres de la **bibliothèque de documents** .

3. Dans la section **paramètres généraux** , cliquez sur le lien paramètres de contrôle de **version** pour afficher la page Paramètres de contrôle de **version** .

4. Vérifiez que le paramètre pour **exiger que les documents soient extraits avant de pouvoir être modifiés** est **non**. Si ce n’est pas le cas, remplacez-le par **non** , puis cliquez sur le bouton **OK** .

5. Fermez le navigateur.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Créer un projet de flux de travail séquentiel SharePoint
 Un flux de travail séquentiel est un ensemble d’étapes qui s’exécute dans l’ordre jusqu’à ce que la dernière activité se termine. Dans cette procédure, nous créons un flux de travail séquentiel qui s’appliquera à notre liste de documents partagés. L’Assistant flux de travail vous permet d’associer le flux de travail à la définition de site ou à la définition de liste et vous permet de déterminer à quel moment le flux de travail doit démarrer.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Pour créer un projet de flux de travail séquentiel SharePoint

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  > **nouveau**  > **projet** pour afficher la boîte de dialogue **nouveau projet** .

3. Développez le nœud **SharePoint** sous **Visual C#**  ou **Visual Basic**, puis choisissez le nœud **2010** .

4. Dans le volet **modèles** , choisissez le modèle de **projet SharePoint 2010** .

5. Dans la zone **nom** , entrez **MySharePointWorkflow** , puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

6. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , choisissez la case **d’option déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.

     Cette étape définit le niveau de confiance de la solution en tant que solution de batterie de serveurs, la seule option disponible pour les projets de Workflow. Pour plus d’informations, consultez [Considérations sur les solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **projet** > **Ajouter un nouvel élément**.

8. Sous **Visual C#**  ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

9. Dans le volet **modèles** , choisissez le modèle **Workflow séquentiel (solution de batterie uniquement)** , puis cliquez sur le bouton **Ajouter** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

10. Dans la page **spécifier le nom du flux de travail pour le débogage** , acceptez le nom par défaut (**MySharePointWorkflow-Workflow1**). Conservez la valeur type de modèle de flux de travail par défaut, **List Workflow**, puis choisissez le bouton **suivant** .

11. Dans la page **voulez-vous que Visual Studio associe automatiquement le flux de travail dans une session de débogage ?** , choisissez le bouton **suivant** pour accepter tous les paramètres par défaut.

     Cette étape associe automatiquement le flux de travail à la bibliothèque de documents partagés.

12. Dans la page **spécifier les conditions de démarrage de votre flux de travail** , laissez les options par défaut sélectionnées dans la section **Comment voulez-vous que le flux de travail démarre ?** , puis choisissez le bouton **Terminer** .

     Cette page vous permet de spécifier à quel moment votre flux de travail démarre. Par défaut, le flux de travail démarre quand un utilisateur le démarre manuellement dans SharePoint ou lorsqu’un élément auquel le flux de travail est associé est créé.

## <a name="create-workflow-activities"></a>Créer des activités de flux de travail
 Les flux de travail contiennent une ou plusieurs *activités* qui représentent des actions à effectuer. Utilisez le concepteur de flux de travail pour organiser les activités d’un flux de travail. Dans cette procédure, nous allons ajouter deux activités au flux de travail : HandleExternalEventActivity et OnWorkflowItemChanged (lors. Ces activités surveillent l’état de la révision des documents dans la liste **documents partagés** .

#### <a name="to-create-workflow-activities"></a>Pour créer des activités de flux de travail

1. Le flux de travail doit s’afficher dans le concepteur de flux de travail. Si ce n’est pas le cas, ouvrez **Workflow1.cs** ou **Workflow1. vb** dans **Explorateur de solutions**.

2. Dans le concepteur, choisissez l’activité **onWorkflowActivated1** .

3. Dans la fenêtre **Propriétés** , entrez **OnWorkflowActivated** en regard de la propriété **appelé** , puis appuyez sur la touche entrée.

     L’éditeur de code s’ouvre et une méthode de gestionnaire d’événements nommée onWorkflowActivated est ajoutée au fichier de code Workflow1.

4. Revenez au concepteur de flux de travail, ouvrez la boîte à outils, puis développez le nœud **Windows Workflow v 3.0** .

5. Dans le nœud **Windows Workflow v 3.0** de la **boîte à outils**, effectuez l’une des opérations suivantes :

    1. Ouvrez le menu contextuel de l’activité **while** , puis choisissez **copier**. Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne sous l’activité **onWorkflowActivated1** , puis choisissez **coller**.

    2. Faites glisser l’activité **while** de la **boîte à outils** vers le concepteur de flux de travail, puis connectez l’activité à la ligne sous l’activité **onWorkflowActivated1** .

6. Choisissez l’activité **WhileActivity1** .

7. Dans la fenêtre **Propriétés** , affectez à **condition** la valeur code.

8. Développez la propriété **condition** , entrez **isWorkflowPending** en regard de la propriété **condition** enfant, puis appuyez sur la touche entrée.

     L’éditeur de code s’ouvre et une méthode nommée isWorkflowPending est ajoutée au fichier de code Workflow1.

9. Revenez au concepteur de flux de travail, ouvrez la boîte à outils, puis développez le nœud **flux de travail SharePoint** .

10. Dans le nœud **flux de travail SharePoint** de la **boîte à outils**, effectuez l’une des opérations suivantes :

    - Ouvrez le menu contextuel de l’activité **OnWorkflowItemChanged (lors** , puis choisissez **copier**. Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne à l’intérieur de l’activité **WhileActivity1** , puis choisissez **coller**.

    - Faites glisser l’activité **OnWorkflowItemChanged (lors** de la **boîte à outils** vers le concepteur de flux de travail, puis connectez l’activité à la ligne à l’intérieur de l’activité **WhileActivity1** .

11. Choisissez l’activité **onWorkflowItemChanged1** .

12. Dans la fenêtre **Propriétés** , définissez les propriétés comme indiqué dans le tableau suivant.

    |Property|valeur|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Appelé**|**OnWorkflowItemChanged (lors**|

## <a name="handle-activity-events"></a>Gérer les événements d’activité
 Enfin, vérifiez l’état du document à partir de chaque activité. Si le document a été révisé, le flux de travail est terminé.

#### <a name="to-handle-activity-events"></a>Pour gérer les événements d’activité

1. Dans *Workflow1.cs* ou *Workflow1. vb*, ajoutez le champ suivant au début de la classe `Workflow1`. Ce champ est utilisé dans une activité pour déterminer si le workflow est terminé.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Ajoutez la méthode suivante à la classe `Workflow1` . Cette méthode vérifie la valeur de la propriété `Document Status` de la liste documents pour déterminer si le document a été révisé. Si la propriété `Document Status` est définie sur `Review Complete`, la méthode `checkStatus` affecte la **valeur false** au champ `workflowPending` pour indiquer que le flux de travail est prêt à se terminer.

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

3. Ajoutez le code suivant aux méthodes `onWorkflowActivated` et `onWorkflowItemChanged` pour appeler la méthode `checkStatus`. Lorsque le flux de travail démarre, la méthode `onWorkflowActivated` appelle la méthode `checkStatus` pour déterminer si le document a déjà été révisé. S’il n’a pas été révisé, le flux de travail continue. Lorsque le document est enregistré, la méthode `onWorkflowItemChanged` appelle à nouveau la méthode `checkStatus` pour déterminer si le document a été révisé. Tandis que le champ `workflowPending` a la valeur **true**, le flux de travail continue à s’exécuter.

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

4. Ajoutez le code suivant à la méthode `isWorkflowPending` pour vérifier l’état de la propriété `workflowPending`. Chaque fois que le document est enregistré, l’activité **WhileActivity1** appelle la méthode `isWorkflowPending`. Cette méthode examine la propriété <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> de l’objet <xref:System.Workflow.Activities.ConditionalEventArgs> pour déterminer si l’activité **WhileActivity1** doit continuer ou se terminer. Si la propriété a la valeur **true**, l’activité se poursuit. Dans le cas contraire, l’activité se termine et le flux de travail se termine.

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

## <a name="test-the-sharepoint-workflow-template"></a>Tester le modèle de flux de travail SharePoint
 Quand vous démarrez le débogueur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie le modèle de flux de travail sur le serveur SharePoint et associe le flux de travail à la liste **documents partagés** . Pour tester le flux de travail, démarrez une instance du flux de travail à partir d’un document dans la liste **documents partagés** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Pour tester le modèle de flux de travail SharePoint

1. Dans *Workflow1.cs* ou *Workflow1. vb*, définissez un point d’arrêt en regard de la méthode **OnWorkflowActivated** .

2. Appuyez sur la touche **F5** pour générer et exécuter la solution.

     Le site SharePoint s’affiche.

3. Dans le volet de navigation de SharePoint, choisissez le lien **documents partagés** .

4. Dans la page **documents partagés** , choisissez le lien **documents** sous l’onglet **outils de bibliothèque** , puis cliquez sur le bouton Télécharger un **document** .

5. Dans la boîte de dialogue **Télécharger un document** , cliquez sur le bouton **Parcourir** , choisissez un fichier de document, cliquez sur le bouton **ouvrir** , puis choisissez le bouton **OK** .

     Cela charge le document sélectionné dans la liste **documents partagés** et démarre le Workflow.

6. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vérifiez que le débogueur s’arrête au point d’arrêt en regard de la méthode `onWorkflowActivated`.

7. Appuyez sur la touche **F5** pour poursuivre l’exécution.

8. Vous pouvez modifier les paramètres du document ici, mais laissez les valeurs par défaut pour le moment en choisissant le bouton **Enregistrer** .

     Cela vous renvoie à la page **documents partagés** du site Web SharePoint par défaut.

9. Dans la page **documents partagés** , vérifiez que la valeur en dessous de la colonne **MySharePointWorkflow-Workflow1** est définie sur **en cours**. Cela indique que le flux de travail est en cours et que le document est en attente de révision.

10. Dans la page **documents partagés** , choisissez le document, cliquez sur la flèche qui s’affiche, puis choisissez l’élément de menu **modifier les propriétés** .

11. Définissez **État du document** sur **Révision terminée**, puis cliquez sur le bouton **Enregistrer** .

     Cela vous renvoie à la page **documents partagés** du site Web SharePoint par défaut.

12. Dans la page **documents partagés** , vérifiez que la valeur sous la colonne **État du document** est définie sur **Révision terminée**. Actualisez la page **documents partagés** et vérifiez que la valeur sous la colonne **MySharePointWorkflow-Workflow1** est définie sur **terminé**. Cela indique que le flux de travail est terminé et que le document a été révisé.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur la création de modèles de flux de travail, consultez les rubriques suivantes :

- Pour en savoir plus sur les activités de flux de travail SharePoint, consultez [activités de flux de travail pour SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Pour en savoir plus sur les activités de Windows Workflow Foundation, consultez [espace de noms System. Workflow. Activities](/dotnet/api/system.workflow.activities&view=netframework-4.8).

## <a name="see-also"></a>Voir aussi
- [Créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
