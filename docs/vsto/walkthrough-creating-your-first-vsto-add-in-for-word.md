---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour Word | Microsoft Docs"
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
  - "Word (développement Office dans Visual Studio), créer un premier projet"
ms.assetid: 9d857be7-5c74-4303-baf4-672afc1ea397
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premier compl&#233;ment VSTO pour Word
  Cette première procédure pas à pas montre comment créer un complément VSTO pour Microsoft Office Word.  Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l'application, quels que soient les documents ouverts.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de complément VSTO Word  
  
-   Écriture d'un code qui utilise le modèle objet de Word pour ajouter du texte à un document quand il est enregistré  
  
-   Génération et exécution du projet à des fins de test  
  
-   Nettoyage du projet terminé pour que le complément VSTO ne s'exécute plus automatiquement sur votre ordinateur de développement  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Création du projet  
  
#### Pour créer un projet de complément VSTO Word dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C\#** ou **Visual Basic**, puis développez **Office\/SharePoint**.  
  
4.  Sous le nœud développé **Office\/SharePoint**, sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de complément VSTO Word.  
  
6.  Dans la zone **Nom**, tapez **PremierComplémentExcel**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **PremierComplémentExcel** et ouvre le fichier de code ThisAddIn dans l'éditeur.  
  
## Écriture d'un code pour ajouter du texte au document enregistré  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn.  Le nouveau code utilise le modèle objet de Word pour ajouter du texte réutilisable dans chaque document enregistré.  Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn`.  Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet de Word.  Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown`.  Ces gestionnaires d'événements sont appelés quand Word charge et décharge votre complément VSTO.  Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé et pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé.  Pour plus d'informations, consultez [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
#### Pour ajouter un paragraphe de texte au document enregistré  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn`.  Le nouveau code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, qui est déclenché quand un document est enregistré.  
  
     Quand l'utilisateur enregistre un document, le gestionnaire d'événements ajoute le nouveau texte au début du document.  
  
     [!code-csharp[Trin_WordAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/VB/ThisAddIn.vb#1)]  
  
    > [!NOTE]  
    >  Ce code utilise une valeur d'index 1 pour accéder au premier paragraphe de la collection <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>.  Bien que Visual Basic et Visual C\# utilisent des tableaux basés sur 0, les limites d'index de tableau inférieures de la plupart des collections du modèle objet Word ont la valeur 1.  Pour plus d'informations, consultez [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).  
  
2.  Si vous utilisez C\#, ajoutez le code requis suivant au gestionnaire d'événements `ThisAddIn_Startup`.  Ce code permet de connecter le gestionnaire d'événements `Application_DocumentBeforeSave` à l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Pour modifier le document quand il est enregistré, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn`.  Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.Word.Application>, qui représente l'instance actuelle de Word.  
  
-   Le paramètre `Doc` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  Le paramètre `Doc` est un objet <xref:Microsoft.Office.Interop.Word.Document> qui représente le document enregistré.  Pour plus d'informations, consultez [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md).  
  
## Test du projet  
  
#### Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet.  Visual Studio crée également un jeu d'entrées du Registre qui permet à Word de détecter et de charger le complément VSTO, et il configure les paramètres de sécurité de l'ordinateur de développement pour permettre au complément VSTO de s'exécuter.  Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans Word, enregistrez le document actif.  
  
3.  Vérifiez que le texte suivant est ajouté au document.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez Word.  
  
## Nettoyage du projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly de complément VSTO, les entrées du Registre et les paramètres de sécurité de votre ordinateur de développement.  Sinon, le complément VSTO s'exécutera chaque fois que vous ouvrirez Word sur votre ordinateur de développement.  
  
#### Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer**, cliquez sur **Nettoyer la solution**.  
  
## Étapes suivantes  
 Maintenant que vous avez créé un complément VSTO de base pour Word, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO : [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Tâches de programmation propres aux compléments VSTO Word : [Solutions Word](../vsto/word-solutions.md).  
  
-   Utilisation du modèle objet de Word : [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md).  
  
-   Personnalisation de l'interface utilisateur de Word en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet de tâches personnalisé : [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des compléments VSTO pour Word : [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de compléments VSTO pour Word : [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Voir aussi  
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  