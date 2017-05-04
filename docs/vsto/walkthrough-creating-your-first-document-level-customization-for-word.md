---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premi&#232;re personnalisation au niveau du document pour Word | Microsoft Docs"
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
  - "personnalisations au niveau du document (développement Office dans Visual Studio), créer un premier projet"
  - "développement Office dans Visual Studio, créer un premier projet"
  - "Word (développement Office dans Visual Studio), créer un premier projet"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de votre premi&#232;re personnalisation au niveau du document pour Word
  Cette procédure pas à pas d'introduction vous indique comment créer une personnalisation au niveau du document pour Microsoft Office Word.  Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un document spécifique est ouvert.  Vous ne pouvez pas utiliser une personnalisation au niveau du document pour apporter des apporter de modifications au niveau de l'application, comme afficher un nouvel onglet de ruban quand un document est ouvert.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de document Word.  
  
-   Ajout de texte au document hébergé dans le concepteur Visual Studio.  
  
-   Écriture de code qui utilise le modèle objet de Word pour ajouter du texte au document personnalisé lorsqu'il est ouvert.  
  
-   Génération et exécution du projet pour le tester.  
  
-   Nettoyage du projet pour supprimer les fichiers de génération inutiles et les paramètres de sécurité de votre ordinateur de développement.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Création du projet  
  
#### Pour créer un projet de document Word dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C\#** ou **Visual Basic**, puis développez **Office\/SharePoint**.  
  
4.  Sous le nœud développé **Office\/SharePoint**, sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de document VSTO Word.  
  
6.  Dans la zone **Nom**, tapez **FirstDocumentCustomization**.  
  
7.  Cliquez sur **OK**.  
  
     L'**Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **Créer un nouveau document**, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstDocumentCustomization**, puis ajoute le document **FirstDocumentCustomization** et le fichier de code ThisDocument au projet.  Le document **FirstDocumentCustomization** est ouvert automatiquement dans le concepteur.  
  
## Fermeture et réouverture du document dans le concepteur  
 Si vous fermez délibérément ou accidentellement le document dans le concepteur pendant que vous développez votre projet, vous pouvez le rouvrir.  
  
#### Pour fermer et rouvrir le document dans le concepteur  
  
1.  Fermez le document en cliquant sur le bouton **Fermer** \(X\) de la fenêtre du concepteur.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code **ThisDocument**, puis cliquez sur **Concepteur de vues**.  
  
     ou  
  
     Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier de code **ThisDocument**.  
  
## Ajout de texte au document dans le concepteur  
 Vous pouvez concevoir l'interface utilisateur de votre personnalisation en modifiant le document qui est ouvert dans le concepteur.  Par exemple, vous pouvez ajouter du texte, des tableaux ou des contrôles Word.  Pour plus d'informations sur l'utilisation du concepteur, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### Pour ajouter du texte à votre document à l'aide du concepteur  
  
1.  Dans le document ouvert dans le concepteur, tapez le texte suivant.  
  
     **This text was added by using the designer.**  
  
## Ajout de texte au document par programmation  
 L'étape suivante consiste à ajouter du code dans le fichier ThisDocument.  Le nouveau code utilise le modèle objet de Word pour ajouter un deuxième paragraphe de texte au document.  Par défaut, le fichier de code ThisDocument contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisDocument`, qui représente le modèle de programmation du document et permet d'accéder au modèle objet de Word.  Pour plus d'informations, consultez [Élément hôte de document](../vsto/document-host-item.md) et [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md).  Le reste de la classe `ThisDocument` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisDocument_Startup` et `ThisDocument_Shutdown`.  Ces gestionnaires d'événements sont appelés à l'ouverture et à la fermeture du document.  Utilisez ces gestionnaires d'événements pour initialiser votre personnalisation à l'ouverture du document et pour nettoyer les ressources utilisées par votre personnalisation à la fermeture du document.  Pour plus d'informations, consultez [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
#### Pour ajouter un deuxième paragraphe de texte au document à l'aide de code  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument**, puis cliquez sur **Afficher le code**.  
  
     Le fichier de code s'ouvre dans Visual Studio.  
  
2.  Remplacez le gestionnaire d'événements `ThisDocument_Startup` par le code suivant.  Lorsque le document s'ouvre, ce code ajoute un deuxième paragraphe de texte au document.  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Ce code utilise la valeur d'index 1 pour accéder au premier paragraphe de la propriété <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>.  Bien que Visual Basic et Visual C\# utilisent des tableaux basés sur 0, les limites d'index de tableau inférieures de la plupart des collections du modèle objet Word ont la valeur 1.  Pour plus d'informations, consultez [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).  
  
## Test du projet  
  
#### Pour tester votre document  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Lorsque vous générez le projet, le code est compilé dans un assembly qui est associé au document.  Visual Studio place une copie du document et l'assembly dans le dossier de sortie de la génération du projet, et il configure les paramètres de sécurité sur l'ordinateur de développement pour permettre l'exécution de la personnalisation.  Pour plus d'informations, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans le document, vérifiez que vous voyez le texte suivant.  
  
     **This text was added by using the designer.**  
  
     **This text was added by using code.**  
  
3.  Fermez le document.  
  
## Nettoyage du projet  
 Lorsque vous avez terminé de développer un projet, vous devez supprimer les fichiers du dossier de sortie de génération et les paramètres de sécurité créés par le processus de génération.  
  
#### Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer**, cliquez sur **Nettoyer la solution**.  
  
## Étapes suivantes  
 Maintenant que vous avez créé une personnalisation de base au niveau du document pour Word, vous pouvez en apprendre plus sur la manière de développer des personnalisations dans les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les personnalisations au niveau du document : [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).  
  
-   Tâches de programmation spécifiques aux personnalisations au niveau du document pour Word : [Solutions Word](../vsto/word-solutions.md).  
  
-   Utilisation du modèle objet de Word : [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md).  
  
-   Personnalisation de l'interface utilisateur de Word en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet Actions : [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Utilisation d'objets Word étendus fournis par les solutions Office dans Visual Studio pour effectuer des tâches qui ne sont pas possibles en utilisant le modèle objet Word \(par exemple, héberger des contrôles managés sur des documents et lier des contrôles Word à des données à l'aide du modèle de liaison de données Windows Forms\) : [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Génération et débogage des personnalisations au niveau du document pour Word :[Génération de solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de personnalisations au niveau du document pour Word :[Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Voir aussi  
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  