---
title: "Proc&#233;dure pas &#224; pas&#160;: automatisation d&#39;une application &#224; partir d&#39;un volet de t&#226;ches personnalis&#233;"
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
helpviewer_keywords: 
  - "volets Office (développement Office dans Visual Studio), PowerPoint"
  - "PowerPoint (développement Office dans Visual Studio), volets Office personnalisés"
  - "automatiser des applications Office"
  - "volets Office personnalisés (développement Office dans Visual Studio), automatisation des applications"
  - "volets Office personnalisés (développement Office dans Visual Studio), PowerPoint"
  - "volets Office (développement Office dans Visual Studio), automatisation des applications"
ms.assetid: 77be5ab5-e330-4564-87ec-9cba564ba8f9
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: automatisation d&#39;une application &#224; partir d&#39;un volet de t&#226;ches personnalis&#233;
  Cette procédure pas à pas montre comment créer un volet Office personnalisé qui automatise PowerPoint. Le volet Office personnalisé insère des dates dans une diapositive quand l’utilisateur clique sur un contrôle <xref:System.Windows.Forms.MonthCalendar> dans le volet Office personnalisé.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement PowerPoint, les concepts présentés ici s’appliquent aux applications listées ci\-dessus.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception de l’interface utilisateur du volet Office personnalisé.  
  
-   Automatisation de PowerPoint à partir du volet Office personnalisé.  
  
-   Affichage du volet Office personnalisé dans PowerPoint.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 ou [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## Création du projet de complément  
 La première étape consiste à créer un projet de complément VSTO pour PowerPoint.  
  
#### Pour créer un projet  
  
1.  Créez un projet de complément PowerPoint VSTO nommé **MyAddIn**, en utilisant le modèle de projet de complément PowerPoint. Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb**, et ajoute le projet **MyAddIn** à l’**Explorateur de solutions**.  
  
## Conception de l’interface utilisateur du volet Office personnalisé  
 Il n’existe aucun concepteur visuel pour les volets Office personnalisés. Toutefois, vous pouvez concevoir un contrôle utilisateur avec la disposition souhaitée. Plus loin dans cette procédure pas à pas, vous allez ajouter le contrôle utilisateur au volet Office personnalisé.  
  
#### Pour concevoir l’interface utilisateur du volet Office personnalisé  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un contrôle utilisateur**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, remplacez le nom du contrôle utilisateur par **MyUserControl**, puis cliquez sur **Ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
3.  Sous l’onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle **MonthCalendar** vers le contrôle utilisateur.  
  
     Si le contrôle **MonthCalendar** est plus grand que l’aire de conception du contrôle utilisateur, redimensionnez le contrôle utilisateur en fonction du contrôle **MonthCalendar**.  
  
## Automatisation de PowerPoint à partir du volet Office personnalisé  
 Le complément VSTO place la date sélectionnée dans la première diapositive de la présentation active. Utilisez l’événement <xref:System.Windows.Forms.MonthCalendar.DateChanged> du contrôle pour ajouter la date sélectionnée chaque fois qu’elle change.  
  
#### Pour automatiser PowerPoint à partir du volet Office personnalisé  
  
1.  Dans le concepteur, double\-cliquez sur le contrôle <xref:System.Windows.Forms.MonthCalendar>.  
  
     Le fichier **MyUserControl.cs** ou **MyUserControl.vb** s’ouvre, et un gestionnaire d’événements est créé pour l’événement <xref:System.Windows.Forms.MonthCalendar.DateChanged>.  
  
2.  Ajoutez le code suivant en haut du fichier. Ce code crée des alias pour les espaces de noms <xref:Microsoft.Office.Core> et <xref:Microsoft.Office.Interop.PowerPoint>.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#1)]  
  
3.  Ajoutez le code suivant à la classe `MyUserControl`. Ce code déclare un objet <xref:Microsoft.Office.Interop.PowerPoint.Shape> en tant que membre de `MyUserControl`. À l’étape suivante, vous allez utiliser <xref:Microsoft.Office.Interop.PowerPoint.Shape> pour ajouter une zone de texte à une diapositive de la présentation active.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#2)]  
  
4.  Remplacez le gestionnaire d'événements `monthCalendar1_DateChanged` par le code suivant. Ce code ajoute une zone de texte à la première diapositive de la présentation active, puis ajoute la date actuellement sélectionnée à la zone de texte. Ce code utilise l’objet `Globals.ThisAddIn` pour accéder au modèle objet de PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#3)]  
  
5.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **MyAddIn**, puis cliquez sur **Générer**. Vérifiez que le projet se génère sans erreur.  
  
## Affichage du volet Office personnalisé  
 Pour afficher le volet Office personnalisé quand le complément VSTO démarre, ajoutez le contrôle utilisateur au volet Office dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.AddIn.Startup> du complément VSTO.  
  
#### Pour afficher le volet Office personnalisé  
  
1.  Dans l’**Explorateur de solutions**, développez **PowerPoint**.  
  
2.  Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb**, puis cliquez sur **Afficher le code**.  
  
3.  Ajoutez le code suivant à la classe `ThisAddIn`. Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#4)]  
  
4.  Remplacez le gestionnaire d'événements `ThisAddIn_Startup` par le code suivant. Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes`. Le code affiche également le volet des tâches.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#5)]  
  
## Test du complément  
 Quand vous exécutez le projet, PowerPoint s’ouvre et le complément VSTO affiche le volet Office personnalisé. Cliquez sur le contrôle <xref:System.Windows.Forms.MonthCalendar> pour tester le code.  
  
#### Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet Office personnalisé est visible.  
  
3.  Cliquez sur une date du contrôle <xref:System.Windows.Forms.MonthCalendar> dans le volet Office.  
  
     La date est insérée dans la première diapositive de la présentation active.  
  
## Étapes suivantes  
 Pour plus d’informations sur la création de volets Office personnalisés, consultez les rubriques suivantes :  
  
-   Créer un volet Office personnalisé dans un complément VSTO pour une autre application. Pour plus d’informations sur les applications qui prennent en charge les volets Office personnalisés, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Créer un bouton de ruban qui permet de masquer ou d’afficher un volet Office personnalisé. Pour plus d'informations, consultez [Procédure pas à pas : synchronisation d'un volet de tâches personnalisé avec un bouton dans le ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Créer un volet Office personnalisé pour chaque message électronique ouvert dans Outlook. Pour plus d'informations, consultez [Procédure pas à pas : affichage de volets des tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## Voir aussi  
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procédure pas à pas : synchronisation d'un volet de tâches personnalisé avec un bouton dans le ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Procédure pas à pas : affichage de volets des tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  