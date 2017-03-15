---
title: "Fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés (Visual Studio), fenêtre Propriétés"
  - "fonctions gestionnaires, fenêtre Propriétés"
  - "gestionnaires, fenêtre Propriétés"
  - "messages Windows"
  - "propriétés (Visual Studio), configuration au moment du design"
  - "propriétés (Visual Studio), modification"
  - "Explorateur de propriétés"
  - "Messages Windows, ajout de gestionnaires de messages"
  - "Propriétés (fenêtre), substitutions"
  - "fonctions virtuelles, fenêtre Propriétés"
  - "Propriétés (fenêtre)"
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez cette fenêtre pour afficher et modifier les propriétés et événements de design d'objets sélectionnés qui sont affichés dans les éditeurs et les concepteurs.  Vous pouvez également utiliser la fenêtre **Propriétés** pour afficher et modifier les propriétés des fichiers, des projets et des solutions.  Vous trouverez la fenêtre **Propriétés** dans le menu **Affichage**.  Vous pouvez également l'ouvrir en appuyant sur F4 ou en tapant Propriétés dans la fenêtre **Lancement rapide**.  
  
 La fenêtre **Propriétés** affiche différents types de champs d'édition, en fonction des besoins d'une propriété particulière.  Ces champs d'édition sont notamment des zones d'édition, des listes déroulantes et des liens vers des boîtes de dialogue d'éditeur personnalisé.  Les propriétés affichées en gris sont en lecture seule.  
  
## Liste UIElement  
 Nom de l'objet  
 Répertorie le ou les objets actuellement sélectionnés.  Seuls les objets de l'éditeur ou du concepteur actif sont visibles.  Lorsque vous sélectionnez plusieurs objets, seules les propriétés communes à tous les objets sélectionnés s'affichent.  
  
 Par catégorie  
 Répertorie, par catégorie, toutes les propriétés et valeurs de propriété pour l'objet sélectionné.  Vous pouvez réduire une catégorie afin de limiter le nombre de propriétés visibles.  Lorsque vous développez ou réduisez une catégorie, un signe plus \(\+\) ou moins \(\-\) s'affiche à gauche du nom de la catégorie.  Les catégories sont répertoriées par ordre alphabétique.  
  
 Alphabétique  
 Trie par ordre alphabétique l'ensemble des propriétés et événement de design pour les objets sélectionnés.  Pour modifier une propriété non estompée, cliquez dans la cellule située à sa droite et entrez les modifications souhaitées.  
  
 Pages de propriétés  
 Affiche la boîte de dialogue **Pages de propriétés** ou **Concepteur de projets** pour l'élément sélectionné.  La boîte de dialogue Pages de propriétés affiche un sous\-ensemble, un ensemble équivalent ou un sur\-ensemble des propriétés disponibles dans la fenêtre **Propriétés**.  Utilisez ce bouton pour afficher et modifier des propriétés relatives à la configuration active de votre projet.  
  
 Propriétés  
 Affiche les propriétés définies pour un objet.  De nombreux objets possèdent également des événements qui peuvent être affichés à l'aide de la fenêtre **Propriétés**.  
  
 Trier par source de propriété  
 Propriétés de groupes par source, telles que l'héritage, les styles appliqués et les liaisons.  Uniquement disponible lors de la modification de fichiers XAML dans le concepteur.  
  
 Événements  
 Affiche les événements définis pour un objet.  
  
> [!NOTE]
>  Ce contrôle de barre d'outils de la fenêtre **Propriétés** n'est disponible que lorsqu'un Concepteur de formulaires ou de contrôles est actif dans le contexte d'un projet [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Lors de la modification de fichiers XAML, les événements apparaissent sous un onglet séparé de la fenêtre de propriétés.  
  
 Messages  
 Répertorie tous les messages Windows.  Vous permet d'ajouter ou de supprimer des fonctions gestionnaires spécifiées pour les messages fournis pour la classe sélectionnée.  
  
> [!NOTE]
>  Ce contrôle de barre d'outils de la fenêtre **Propriétés** n'est disponible que lorsque la fenêtre active est **Affichage de classes**, dans le contexte d'un projet [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)].  
  
 Overrides  
 Répertorie toutes les fonctions virtuelles de la classe sélectionnée, et vous permet d'ajouter ou de supprimer des fonctions de substitution.  
  
> [!NOTE]
>  Ce contrôle de barre d'outils de la fenêtre **Propriétés** n'est disponible que lorsque la fenêtre active est **Affichage de classes**, dans le contexte d'un projet [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)].  
  
 Volet Description  
 Présente le type de la propriété et la décrit brièvement.  Vous pouvez activer et désactiver la description de la propriété à l'aide de la commande Description du menu contextuel.  
  
> [!NOTE]
>  Ce contrôle de barre d'outils de la fenêtre **Propriétés** n'est pas disponible lors de la modification de fichiers XAML dans le concepteur.  
  
 Affichage en miniature  
 Affiche une représentation visuelle de l'élément actuellement sélectionné lors de la modification des fichiers XAML dans le concepteur.  
  
 Rechercher  
 Fournit une fonction de recherche pour les propriétés et événements lors de la modification de fichiers XAML dans le concepteur.  La zone de recherche répond aux recherches de correspondance partielle de texte et met à jour les résultats de la recherche au fur et à mesure de la saisie.  
  
## Voir aussi  
 [Référence de propriétés de projet](../../ide/reference/project-properties-reference.md)   
 [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)