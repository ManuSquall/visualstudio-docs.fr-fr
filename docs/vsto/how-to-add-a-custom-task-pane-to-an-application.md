---
title: "Comment&#160;: ajouter un volet de t&#226;ches personnalis&#233; &#224; une application | Microsoft Docs"
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
  - "volets de tâches personnalisés (développement Office dans Visual Studio), ajouter à une application"
  - "volets de tâches (développement Office dans Visual Studio), ajouter à une application"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Comment&#160;: ajouter un volet de t&#226;ches personnalis&#233; &#224; une application
  Vous pouvez ajouter un volet des tâches personnalisé aux applications répertoriées ci\-dessus à l'aide du complément VSTO.  Pour plus d'informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Ajout d'un volet des tâches personnalisé à une application  
  
#### Pour ajouter un volet des tâches personnalisé à une application  
  
1.  Ouvrez ou créez un projet de complément VSTO pour l'une des applications répertoriées ci\-dessus.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un contrôle utilisateur**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, remplacez le nom du nouveau contrôle utilisateur par **MyUserControl**, puis cliquez sur **Ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
4.  Ajoutez un ou plusieurs contrôles Windows Forms de la **Boîte à outils** au contrôle utilisateur.  
  
5.  Ouvrez le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb**.  
  
6.  Ajoutez le code suivant à la classe `ThisAddIn`.  Ce code déclare des instances de `MyUserControl` et <xref:Microsoft.Office.Tools.CustomTaskPane> en tant que membres de la classe `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  Ajoutez le code ci\-après au gestionnaire d'événements `ThisAddIn_Startup`.  Ce code crée <xref:Microsoft.Office.Tools.CustomTaskPane> en ajoutant l'objet `MyUserControl` à la collection `CustomTaskPanes`.  Le code affiche également le volet des tâches.  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  Ce code associe votre volet des tâches personnalisé à la fenêtre active de l'application.  Pour certaines applications, vous pouvez modifier ce code afin de vous assurer que le volet des tâches s'affiche avec les autres documents ou éléments de l'application.  Pour plus d'informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
## Voir aussi  
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Procédure pas à pas : automatisation d'une application à partir d'un volet de tâches personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  