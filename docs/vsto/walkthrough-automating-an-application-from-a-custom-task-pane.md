---
title: "Procédure pas à pas : Automatisation d’une Application à partir d’un volet Office personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 86f925cda43bf73354b94ecc966cdcae1a0c3ddd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-automating-an-application-from-a-custom-task-pane"></a>Procédure pas à pas : automatisation d'une application à partir d'un volet de tâches personnalisé
  Cette procédure pas à pas montre comment créer un volet Office personnalisé qui automatise PowerPoint. Le volet Office personnalisé insère des dates dans une diapositive quand l’utilisateur clique sur un contrôle <xref:System.Windows.Forms.MonthCalendar> dans le volet Office personnalisé.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement PowerPoint, les concepts présentés ici s’appliquent aux applications listées ci-dessus.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception de l’interface utilisateur du volet Office personnalisé.  
  
-   Automatisation de PowerPoint à partir du volet Office personnalisé.  
  
-   Affichage du volet Office personnalisé dans PowerPoint.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 ou [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="creating-the-add-in-project"></a>Création du projet de complément  
 La première étape consiste à créer un projet de complément VSTO pour PowerPoint.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de complément PowerPoint VSTO nommé **MyAddIn**, en utilisant le modèle de projet de complément PowerPoint. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb** , et ajoute le projet **MyAddIn** à l’ **Explorateur de solutions**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Conception de l’interface utilisateur du volet Office personnalisé  
 Il n’existe aucun concepteur visuel pour les volets Office personnalisés. Toutefois, vous pouvez concevoir un contrôle utilisateur avec la disposition de votre choix. Ultérieurement dans cette procédure, vous ajouterez le contrôle utilisateur au volet Office personnalisé.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Pour concevoir l’interface utilisateur du volet Office personnalisé  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom du contrôle utilisateur par **MyUserControl**, puis cliquez sur **Ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
3.  Sous l’onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle **MonthCalendar** vers le contrôle utilisateur.  
  
     Si le contrôle **MonthCalendar** est plus grand que l’aire de conception du contrôle utilisateur, redimensionnez le contrôle utilisateur en fonction du contrôle **MonthCalendar** .  
  
## <a name="automating-powerpoint-from-the-custom-task-pane"></a>Automatisation de PowerPoint à partir du volet Office personnalisé  
 Le complément VSTO place la date sélectionnée dans la première diapositive de la présentation active. Utilisez l’événement <xref:System.Windows.Forms.MonthCalendar.DateChanged> du contrôle pour ajouter la date sélectionnée chaque fois qu’elle change.  
  
#### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Pour automatiser PowerPoint à partir du volet Office personnalisé  
  
1.  Dans le concepteur, double-cliquez sur le contrôle <xref:System.Windows.Forms.MonthCalendar> .  
  
     Le fichier **MyUserControl.cs** ou **MyUserControl.vb** s’ouvre, et un gestionnaire d’événements est créé pour l’événement <xref:System.Windows.Forms.MonthCalendar.DateChanged> .  
  
2.  Ajoutez le code suivant en haut du fichier. Ce code crée des alias pour les espaces de noms <xref:Microsoft.Office.Core> et <xref:Microsoft.Office.Interop.PowerPoint> .  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Ajoutez le code suivant à la classe `MyUserControl` . Ce code déclare un objet <xref:Microsoft.Office.Interop.PowerPoint.Shape> en tant que membre de `MyUserControl`. À l’étape suivante, vous allez utiliser <xref:Microsoft.Office.Interop.PowerPoint.Shape> pour ajouter une zone de texte à une diapositive de la présentation active.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Remplacez le gestionnaire d'événements `monthCalendar1_DateChanged` par le code suivant. Ce code ajoute une zone de texte à la première diapositive de la présentation active, puis ajoute la date actuellement sélectionnée à la zone de texte. Ce code utilise l’objet `Globals.ThisAddIn` pour accéder au modèle objet de PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **MyAddIn** , puis cliquez sur **Générer**. Vérifiez que le projet se génère sans erreur.  
  
## <a name="displaying-the-custom-task-pane"></a>Affichage du volet Office personnalisé  
 Pour afficher le volet Office personnalisé quand le complément VSTO démarre, ajoutez le contrôle utilisateur au volet Office dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.AddIn.Startup> du complément VSTO.  
  
#### <a name="to-display-the-custom-task-pane"></a>Pour afficher le volet Office personnalisé  
  
1.  Dans l’ **Explorateur de solutions**, développez **PowerPoint**.  
  
2.  Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb** , puis cliquez sur **Afficher le code**.  
  
3.  Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn` .  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Remplacez le gestionnaire d'événements `ThisAddIn_Startup` par le code suivant. Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes` . Le code affiche également le volet des tâches.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="testing-the-add-in"></a>Test du complément  
 Quand vous exécutez le projet, PowerPoint s’ouvre et le complément VSTO affiche le volet Office personnalisé. Cliquez sur le contrôle <xref:System.Windows.Forms.MonthCalendar> pour tester le code.  
  
#### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet Office personnalisé est visible.  
  
3.  Cliquez sur une date du contrôle <xref:System.Windows.Forms.MonthCalendar> dans le volet Office.  
  
     La date est insérée dans la première diapositive de la présentation active.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur la création de volets Office personnalisés, consultez les rubriques suivantes :  
  
-   Créer un volet Office personnalisé dans un complément VSTO pour une autre application. Pour plus d’informations sur les applications qui prennent en charge les volets de tâches personnalisés, consultez [les volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Créer un bouton de ruban qui permet de masquer ou d’afficher un volet Office personnalisé. Pour plus d'informations, consultez [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Créer un volet Office personnalisé pour chaque message électronique ouvert dans Outlook. Pour plus d'informations, consultez [Walkthrough: Displaying Custom Task Panes with E-Mail Messages in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Comment : ajouter un volet Office personnalisé à une Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procédure pas à pas : Synchronisation d’un volet Office personnalisé avec un bouton du ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Procédure pas à pas : affichage de volets de tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  