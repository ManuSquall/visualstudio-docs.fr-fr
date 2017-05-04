---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour Project | Microsoft Docs"
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
  - "compléments de niveau application (développement Office dans Visual Studio), créer votre premier projet"
  - "développement Office dans Visual Studio, créer votre premier projet"
  - "Project (développement Office dans Visual Studio), créer votre premier projet"
  - "compléments (développement Office dans Visual Studio) créer votre premier projet"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour Project
  Cette procédure pas à pas vous montre comment créer un complément VSTO pour Microsoft Office Project. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l’application proprement dite, quels que soient les projets ouverts. Pour plus d'informations, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet de complément VSTO Project  
  
-   Écriture de code qui utilise le modèle objet de Project pour ajouter une tâche à un nouveau projet  
  
-   Génération et exécution du projet pour le tester  
  
-   Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] ou [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## Création du projet  
  
#### Pour créer un projet dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C\#** ou **Visual Basic**, puis développez **Office\/SharePoint**.  
  
4.  Sous le nœud développé **Office\/SharePoint**, sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez **Complément Project 2010** ou **Complément Project 2013**.  
  
6.  Dans la zone **Nom**, tapez **FirstProjectAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstProjectAddIn** et ouvre le fichier de code **ThisAddIn** dans l’éditeur.  
  
## Écriture de code qui ajoute une nouvelle tâche à un projet  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de Project pour ajouter une nouvelle tâche à un projet. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn`. Cette classe fournit un point d’entrée pour votre code et donne accès au modèle objet de Project. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown`. Ces gestionnaires d’événements sont appelés quand Project charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d'informations, consultez [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
#### Pour ajouter une tâche à un nouveau projet  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn`. Ce code définit un gestionnaire d’événements pour l’événement NewProject de la classe Microsoft.Office.Interop.MSProject.Application.  
  
     Quand l’utilisateur crée un projet, ce gestionnaire d’événements ajoute une tâche au projet.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 Pour modifier le projet, cet exemple de code utilise les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn`. Le champ `Application` retourne un objet Microsoft.Office.Interop.MSProject.Application qui représente l’instance active de Project.  
  
-   Le paramètre `pj` du gestionnaire d'événements pour l'événement NewProject. Le paramètre `pj` est un objet Microsoft.Office.Interop.MSProject.Project qui représente le projet. Pour plus d'informations, consultez [Solutions Project](../vsto/project-solutions.md).  
  
1.  En C\#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup`. Ce code connecte le gestionnaire d’événements `Application_Newproject` avec l’événement NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## Test du projet  
 Quand vous générez et exécutez le projet, vérifiez que la nouvelle tâche apparaît dans le nouveau projet obtenu.  
  
#### Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet. Microsoft Project démarre et ouvre automatiquement un nouveau projet vide.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée aussi un jeu d’entrées de Registre qui permet à Project de détecter et de charger le complément VSTO, puis configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution du complément VSTO. Pour plus d'informations, consultez [Vue d'ensemble du processus de génération de solutions Office](http://msdn.microsoft.com/fr-fr/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Vérifiez qu’une nouvelle tâche est bien ajoutée au projet vierge.  
  
3.  Vérifiez que le texte suivant s’affiche dans le champ **Nom de la tâche** de la tâche.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez Microsoft Project.  
  
## Nettoyage du projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécute chaque fois que vous ouvrez Microsoft Project sur votre ordinateur.  
  
#### Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer**, cliquez sur **Nettoyer la solution**.  
  
## Étapes suivantes  
 Maintenant que vous avez créé un complément VSTO de base pour Project, vous pouvez en savoir plus sur le développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour Project : [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet de Project : [Solutions Project](../vsto/project-solutions.md).  
  
-   Génération et débogage des compléments VSTO pour Project : [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement des compléments VSTO pour Project : [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
## Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Solutions Project](../vsto/project-solutions.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  