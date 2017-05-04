---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour PowerPoint | Microsoft Docs"
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
  - "compléments (développement Office dans Visual Studio), créer un premier projet"
  - "compléments d'application (développement Office dans Visual Studio), créer un premier projet"
  - "développement Office dans Visual Studio, créer un premier projet"
  - "PowerPoint (développement Office dans Visual Studio), créer un premier projet"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour PowerPoint
  Cette procédure pas à pas montre comment créer un complément VSTO pour Microsoft Office PowerPoint.  Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l'application, quelles que soient les présentations ouvertes.  Pour plus d'informations, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   création d'un projet de complément PowerPoint VSTO pour PowerPoint ;  
  
-   écriture de code utilisant le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive ;  
  
-   Génération et exécution du projet pour le tester.  
  
-   nettoyage du projet pour que le complément VSTO ne s'exécute plus automatiquement sur votre ordinateur de développement.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## Création du projet  
  
#### Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C\#** ou **Visual Basic**, puis développez **Office\/SharePoint**.  
  
4.  Sous le nœud développé **Office\/SharePoint**, sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de complément PowerPoint VSTO.  
  
6.  Dans la zone **Nom**, tapez **FirstPowerPointAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstPowerPointAddIn** et ouvre le fichier de code **ThisAddIn** dans l'éditeur.  
  
## Écriture du code qui ajoute du texte à chaque nouvelle diapositive  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn.  Le nouveau code utilise le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive.  Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn`.  Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet de PowerPoint.  Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown`.  Ces gestionnaires d'événements sont appelés quand PowerPoint charge et décharge votre complément VSTO.  Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé.  Pour plus d'informations, consultez [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
#### Pour ajouter une zone de texte à chaque nouvelle diapositive  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn`.  Ce code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> de l'objet <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Quand l'utilisateur ajoute une nouvelle diapositive à la présentation active, ce gestionnaire d'événements ajoute une zone de texte en haut de la nouvelle diapositive, puis ajoute du texte à la zone de texte.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  En C\#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup`.  Ce code est indispensable pour connecter le gestionnaire d'événements `Application_PresentationNewSlide` à l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Pour modifier chaque nouvelle diapositive, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn`.  Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint.  
  
-   Le paramètre `Sld` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  Le paramètre `Sld` est un objet <xref:Microsoft.Office.Interop.PowerPoint.Slide>, qui représente la nouvelle diapositive.  Pour plus d'informations, consultez [Solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
## Test du projet  
 Quand vous générez et exécutez le projet, vérifiez que la zone de texte apparaît dans les nouvelles diapositives que vous ajoutez à une présentation.  
  
#### Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est placé dans le dossier de sortie de la génération du projet.  Visual Studio crée également un jeu d'entrées du Registre qui permet à PowerPoint de détecter et de charger le complément VSTO. Par ailleurs, il configure les paramètres de sécurité de l'ordinateur de développement pour permettre au complément VSTO de s'exécuter.  Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans PowerPoint, ajoutez une nouvelle diapositive à la présentation active.  
  
3.  Vérifiez que le texte suivant est ajouté à une nouvelle zone de texte en haut de la diapositive.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez PowerPoint.  
  
## Nettoyage du projet  
 Une fois que vous avez fini de développer un projet, supprimez l'assembly de complément VSTO, les entrées du Registre et les paramètres de sécurité de votre ordinateur de développement.  Sinon, le complément VSTO s'exécutera chaque fois que vous ouvrirez PowerPoint sur votre ordinateur.  
  
#### Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer**, cliquez sur **Nettoyer la solution**.  
  
## Étapes suivantes  
 Une fois que vous avez créé un complément VSTO de base pour PowerPoint, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour PowerPoint.  Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet de PowerPoint.  Pour plus d'informations, consultez [Solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personnalisation de l'interface utilisateur de PowerPoint en ajoutant un onglet personnalisé au ruban, ou en créant votre propre volet des tâches personnalisé.  Pour plus d'informations, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des compléments VSTO pour PowerPoint.  Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement des compléments VSTO pour PowerPoint.  Pour plus d'informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Voir aussi  
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Solutions PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  