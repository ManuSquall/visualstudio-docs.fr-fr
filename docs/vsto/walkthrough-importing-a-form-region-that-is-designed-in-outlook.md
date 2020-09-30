---
title: 'Procédure pas à pas : importer une zone de formulaire conçue dans Outlook'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a0de1a25a5309e99193b7be8bce2819808665b8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584974"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Procédure pas à pas : importer une zone de formulaire conçue dans Outlook
  Cette procédure pas à pas montre comment concevoir une zone de formulaire dans Microsoft Office Outlook, puis importer la zone de formulaire dans un projet de complément VSTO Outlook à l’aide de l’Assistant **Nouvelle zone de formulaire** . La conception de la zone de formulaire dans Outlook vous permet d’ajouter des contrôles Outlook natifs à la zone de formulaire liée aux données Outlook. Après avoir importé la zone de formulaire, vous pouvez gérer les événements de chaque contrôle.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- conception d’une zone de formulaire à l’aide du Concepteur de zones de formulaire dans Outlook ;

- importation d’une zone de formulaire dans un projet de complément VSTO Outlook ;

- gestion des événements des contrôles dans la zone de formulaire.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] ou [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Concevoir une zone de formulaire à l’aide du concepteur de zones de formulaire dans Outlook
 Dans cette étape, vous allez concevoir une zone de formulaire dans Outlook. Vous enregistrerez ensuite la zone de formulaire à un emplacement facile à trouver pour pouvoir l’importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Cet exemple de zone de formulaire remplace complètement le formulaire de tâche habituel. Il fournit un moyen de suivre la progression de toutes les tâches qui doivent être effectuées pour permettre l’exécution de la tâche principale (tâches préalables). La zone de formulaire affiche une liste des tâches préalables, ainsi que l’état d’achèvement de chaque tâche dans la liste. Les utilisateurs peuvent ajouter des tâches à la liste, et en supprimer. Ils peuvent également actualiser l’état d’achèvement de chaque tâche.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Pour concevoir une zone de formulaire à l’aide du Concepteur de zones de formulaire dans Outlook

1. Démarrez Microsoft Office Outlook.

2. Dans Outlook, sous l’onglet **Développeur** cliquez sur **Créer un formulaire**. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Dans la zone **Créer un formulaire** , cliquez sur **Tâche**, puis sur **Ouvrir**.

4. Dans Outlook, sous l’onglet **Développeur** , dans le groupe **Créer** , cliquez sur **Nouvelle zone de formulaire**.

     Une nouvelle zone de formulaire s’ouvre. Si le **Sélecteur de champs** n’apparaît pas, cliquez sur **Sélecteur de champs** dans le groupe **Outils** .

5. Faites glisser le champ **Objet** et le champ **% achevé** du **Sélecteur de champs** vers la zone de formulaire.

6. Dans le groupe **Outils** , cliquez sur **Boîte à outils Contrôles** pour ouvrir la **Boîte à outils**.

7. Faites glisser une étiquette de la **Boîte à outils** vers la zone de formulaire. Placez l’étiquette sous les champs **Objet** et **% achevé** .

8. Cliquez avec le bouton droit sur l’étiquette, puis cliquez sur **Propriétés avancées**.

9. Dans la fenêtre **Propriétés** , affectez à la propriété **Caption** la valeur **Cette tâche dépend des tâches suivantes**, affectez à la propriété **Width** la valeur **200**, puis cliquez sur **Appliquer**.

10. Faites glisser un contrôle ListBox de la **Boîte à outils** vers la zone de formulaire. Placez la zone de liste sous l’étiquette **Cette tâche dépend des tâches suivantes** .

11. Sélectionnez la zone de liste que vous venez d’ajouter.

12. Dans la fenêtre **Propriétés** , affectez à **Width** la valeur **300**, puis cliquez sur **Appliquer**.

13. Faites glisser une étiquette de la **Boîte à outils** vers la zone de formulaire. Placez l’étiquette sous la zone de liste.

14. Sélectionnez l’étiquette que vous venez d’ajouter.

15. Dans la fenêtre **Propriétés** , affectez à la propriété **Caption** la valeur **Sélectionnez une tâche à ajouter à la liste des tâches dépendantes**, affectez à la propriété **Width** la valeur **200**, puis cliquez sur **Appliquer**.

16. Faites glisser un contrôle ComboBox de la **Boîte à outils** vers la zone de formulaire. Placez la zone de liste modifiable sous l’étiquette **Sélectionnez une tâche à ajouter à la liste des tâches dépendantes** .

17. Sélectionnez la zone de liste modifiable que vous venez d’ajouter.

18. Dans la fenêtre **Propriétés** , affectez à la propriété **Width** la valeur **300**, puis cliquez sur **Appliquer**.

19. Faites glisser un contrôle CommandButton de la **Boîte à outils** vers la zone de formulaire. Placez le bouton de commande à côté de la zone de liste modifiable.

20. Sélectionnez le bouton de commande que vous venez d’ajouter.

21. Dans la fenêtre **Propriétés** , affectez à **Name** la valeur **AddDependentTask**, affectez à **Caption** la valeur **Ajouter une tâche dépendante**, affectez à **Width** la valeur **100**, puis cliquez sur **Appliquer**.

22. Dans le **Sélecteur de champs**, cliquez sur **Nouveau**.

23. Dans la boîte de dialogue **Nouveau champ** , tapez **hiddenField** dans le champ **Nom** , puis cliquez sur **OK**.

24. Faites glisser le champ **hiddenField** du **Sélecteur de champs** vers la zone de formulaire.

25. Dans la fenêtre **Propriétés** , affectez à **Visible** la valeur **0 - False**, puis cliquez sur **Appliquer**.

26. Dans Outlook, sous l’onglet **Développeur** , dans le groupe **Créer** , cliquez sur le bouton **Enregistrer** , puis sur **Enregistrer la zone de formulaire sous**.

     Nommez la zone de formulaire **TaskFormRegion** , puis enregistrez-la dans un répertoire local sur votre ordinateur.

     Outlook enregistre la zone de formulaire sous la forme d’un fichier de stockage de formulaire Outlook (*. OFS*). La zone de formulaire est enregistrée sous le nom *TaskFormRegion. OFS*.

27. Quittez Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Créer un projet de complément Outlook
 Dans cette étape, vous allez créer un projet de complément VSTO Outlook. Plus loin dans cette procédure pas à pas, vous allez importer la zone de formulaire dans le projet.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Outlook

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément VSTO Outlook, et nommez-le **TaskAddIn**.

2. Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Créer le répertoire pour la solution**.

3. Enregistrez le projet dans le répertoire de projet par défaut.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importer la zone de formulaire
 Vous pouvez importer la zone de formulaire conçue dans Outlook dans le projet de complément VSTO Outlook à l’aide de l’Assistant **Nouvelle zone de formulaire Outlook** .

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Pour importer la zone de formulaire dans le projet de complément VSTO Outlook

1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TaskAddIn** , pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.

2. Dans le volet **Modèle** , sélectionnez **Zone de formulaire Outlook**, nommez le fichier **TaskFormRegion**, puis cliquez sur **Ajouter**.

     L’Assistant **zone de formulaire NewOutlook** démarre.

3. Dans la page **Sélectionnez la méthode de création de la zone de formulaire** , cliquez sur **Importer un fichier de stockage de formulaire Outlook (.ofs)**, puis sur **Parcourir**.

4. Dans la boîte de dialogue **Emplacement du fichier de zone du formulaire Outlook existant** , accédez à l’emplacement de *TaskFormRegion.ofs*, sélectionnez **TaskFormRegion.ofs**, cliquez sur **Ouvrir**, puis sur **Suivant**.

5. Dans la page **Sélectionnez le type de zone de formulaire que vous souhaitez créer** , cliquez sur **Remplacement global**, puis sur **Suivant**.

     Une zone de formulaire de type *Remplacement global* remplace l’intégralité du formulaire Outlook. Pour plus d’informations sur les types de zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

6. Dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d’affichage** , cliquez sur **Suivant**.

7. Dans la page **Identifiez les classes de message qui afficheront cette zone de formulaire** , dans le champ **Quelles classes de message personnalisées afficheront cette zone de formulaire ?** , tapez **IPM.Task.TaskFormRegion**, puis cliquez sur **Terminer**.

     Un fichier *TaskFormRegion.cs* ou *TaskFormRegion. vb* est ajouté à votre projet.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Gérer les événements de contrôles sur la zone de formulaire
 Une fois que la zone de formulaire se trouve dans le projet, vous pouvez ajouter du code pour gérer l’événement `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` du bouton que vous avez ajouté à la zone de formulaire dans Outlook.

 Ajoutez également du code à l’événement <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> qui met à jour les contrôles de la zone de formulaire quand celle-ci s’affiche.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Pour gérer les événements des contrôles dans la zone de formulaire

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *TaskFormRegion.cs* ou sur *TaskFormRegion. vb*, puis cliquez sur **afficher le code**.

    *TaskFormRegion.cs* ou *TaskFormRegion. vb* s’ouvre dans l’éditeur de code.

2. Ajoutez le code suivant à la classe `TaskFormRegion` . Ce code remplit la zone de liste modifiable de la zone de formulaire à l’aide de la ligne d’objet de chaque tâche du dossier Tâches d’Outlook.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Ajoutez le code suivant à la classe `TaskFormRegion` . Ce code effectue les tâches suivantes :

   - Localise l’emplacement de `Microsoft.Office.Interop.Outlook.TaskItem` dans le dossier Tâches en appelant la méthode d’assistance `FindTaskBySubjectName` et en passant l’objet de la tâche souhaitée. Vous allez ajouter la méthode d’assistance `FindTaskBySubjectName` durant la prochaine étape.

   - Ajoute les valeurs `Microsoft.Office.Interop.Outlook.TaskItem.Subject` et `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` à la zone de liste des tâches dépendantes.

   - Ajoute l’objet de la tâche au champ masqué dans la zone de formulaire. Le champ masqué stocke ces valeurs dans le cadre de l’élément Outlook.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Ajoutez le code suivant à la classe `TaskFormRegion` . Ce code fournit la méthode d’assistance `FindTaskBySubjectName` décrite à l’étape précédente.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Ajoutez le code suivant à la classe `TaskFormRegion` . Ce code effectue les tâches suivantes :

   - Actualise la zone de liste de la zone de formulaire à l’aide de l’état d’achèvement actuel de chaque tâche dépendante.

   - Analyse le champ de texte masqué pour obtenir l’objet de chaque tâche dépendante. Il localise ensuite chaque `Microsoft.Office.Interop.Outlook.TaskItem` dans le dossier *tâches* en appelant la `FindTaskBySubjectName` méthode d’assistance et en passant l’objet de chaque tâche.

   - Ajoute les valeurs `Microsoft.Office.Interop.Outlook.TaskItem.Subject` et `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` à la zone de liste des tâches dépendantes.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. Remplacez le gestionnaire d'événements `TaskFormRegion_FormRegionShowing` par le code suivant. Ce code effectue les tâches suivantes :

   - Remplit la zone de liste modifiable de la zone de formulaire à l’aide des objets de tâche, une fois que la zone de formulaire s’affiche.

   - Appelle la méthode d’assistance `RefreshTaskListBox` quand la zone de formulaire s’affiche. Cela entraîne l’affichage de toutes les tâches dépendantes ajoutées à la zone de liste quand l’élément a été ouvert pour la dernière fois.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Tester la zone de formulaire Outlook
 Pour tester la zone de formulaire, ajoutez des tâches à la liste des tâches préalables dans la zone de formulaire. Mettez à jour l’état d’achèvement d’une tâche préalable, puis affichez l’état d’achèvement mis à jour de la tâche dans la liste des tâches préalables.

### <a name="to-test-the-form-region"></a>Pour tester la zone de formulaire

1. Appuyez sur **F5** pour exécuter le projet.

     Outlook démarre.

2. Dans Outlook, sous l’onglet **Accueil** , cliquez sur **Nouveaux éléments**, puis sur **Tâche**.

3. Dans le formulaire de tâche, tapez **Tâche dépendante** dans le champ **Objet** .

4. Sous l’onglet **tâche** du ruban, dans le groupe **actions** , cliquez sur **Enregistrer & fermer**.

5. Dans Outlook, sous l’onglet **Accueil** , cliquez sur **Nouveaux éléments**, sur **Autres éléments**, puis sur **Choisir un formulaire**.

6. Dans la boîte de dialogue **Choisir un formulaire** , cliquez sur **TaskFormRegion**, puis sur **Ouvrir**.

     La zone de formulaire **TaskFormRegion** s’affiche. Ce formulaire remplace l’intégralité du formulaire de tâche. La zone de liste modifiable **Sélectionnez une tâche à ajouter à la liste des tâches dépendantes** est remplie à l’aide des autres tâches du dossier Tâches.

7. Dans le formulaire de tâche, dans le champ **Objet** , tapez **Tâche principale**.

8. Dans la zone de liste modifiable **Sélectionnez une tâche à ajouter à la liste des tâches dépendantes** , sélectionnez **Tâche dépendante**, puis cliquez sur **Ajouter une tâche dépendante**.

     **Achevée à 0 % -- Tâche dépendante** s’affiche dans la zone de liste **Cette tâche dépend des tâches suivantes** . Cela montre que vous avez correctement géré l’événement `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` du bouton.

9. Enregistrez et fermez l’élément **Tâche principale** .

10. Rouvrez l’élément Tâche dépendante dans Outlook.

11. Dans le formulaire de tâche dépendante, remplacez la valeur du champ **% achevé** par **50 %**.

12. Sous l’onglet **tâche** du ruban tâches dépendantes, dans le groupe **actions** , cliquez sur **Enregistrer & fermer**.

13. Rouvrez l’élément **Tâche principale** dans Outlook.

     **Achevée à 50 % -- Tâche dépendante** s’affiche désormais dans la zone de liste **Cette tâche dépend des tâches suivantes** .

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'une application Outlook, consultez les rubriques suivantes :

- Pour en savoir plus sur la façon de concevoir l’apparence d’une zone de formulaire en faisant glisser des contrôles managés vers un concepteur visuel, consultez [procédure pas à pas : concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Pour en savoir plus sur la personnalisation du ruban d’un élément Outlook, consultez [personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

- Pour en savoir plus sur l’ajout d’un volet de tâches personnalisé à Outlook, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
