---
title: "Comment&#160;: cr&#233;er et modifier des configurations | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurations de build, créer"
  - "configurations de build, modifier"
  - "générations (Visual Studio), configurer"
  - "Gestionnaire de configurations"
  - "configurations de build de projet, créer"
  - "configurations de build de projet, modifier"
  - "pages de propriétés"
  - "configurations de build de solution, créer"
  - "configurations de build de solution, modifier"
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er et modifier des configurations
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Créez plusieurs configurations de build pour une solution.  Par exemple, configurez une version Debug que les testeurs utiliseront pour rechercher et résoudre les problèmes, vous pouvez également configurer différents types de builds pour les distribuer à différents clients.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Création de configurations de build  
 Vous pouvez utiliser la boîte de dialogue **Gestionnaire de configurations** pour sélectionner ou modifier des configurations de build existantes, ou vous pouvez en créer de nouveaux.  
  
#### Pour ouvrir la boîte de dialogue du Gestionnaire de configurations  
  
-   Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour la solution puis choisissez **Configuration Manager**.  
  
    > [!NOTE]
    >  Si la commande **Gestionnaire de configurations** n'apparaît pas dans le menu contextuel, regardez sous le menu **Build** dans la barre de menus.  Si elle n'apparaît pas là non plus, dans la barre de menus, sélectionnez **Outils**, **Options**, puis dans le volet gauche de la boîte de dialogue **Options**, développez les onglets **Projets et solutions**, **Général**, et dans le volet droit, activez **Afficher les configurations de build avancées**.  
  
     Dans la boîte de dialogue **Gestionnaire de configurations**, utilisez la liste déroulante **Configuration de la solution active** pour sélectionner une configuration de build correspondant à la solution, pour modifier la configuration existante, ou en créer une nouvelle.  Vous pouvez utiliser la liste déroulante **Plateforme de la solution active** pour sélectionner la plateforme que la configuration cible, modifier la plateforme existante, ou en ajouter une nouvelle.  Le volet **Contextes des projets** répertorie les projets de la solution.  Pour chaque projet, sélectionnez une configuration et une plateforme spécifique au projet, en modifier des versions existantes, créer une nouvelle configuration ou ajouter une nouvelle plateforme.  Egalement, cochez les cases qui indiquent si chaque projet est inclus lorsque vous utilisez la configuration correspondant à la solution pour générer ou déployer celle\-ci.  
  
 Après avoir installé les configurations que vous souhaitez, définissez les propriétés de projet appropriées pour ces configurations.  
  
#### Pour définir des propriétés sur la base de configurations  
  
-   Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour un projet et choisissez **Propriétés**.  
  
     La fenêtre  **Pages de propriétés** s'ouvre.  
  
     Définissez des propriétés pour vos configurations.  Par exemple, pour une configuration Release, vous pouvez spécifier que le code est optimisé lorsque la solution est générée, et une configuration de Debug, vous pouvez spécifier que le symbole de compilation conditionnelle `DEBUG` est inclus.  Pour plus d'informations concernant les paramètres de la page de propriétés, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## Création et modification des configurations d'un projet.  
  
#### Pour créer une configuration de projet  
  
1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.  
  
2.  Sélectionnez un projet dans la colonne **Projet**.  
  
3.  Dans la liste déroulante **Configuration** correspondant à ce projet, choisissez **Nouveau**.  
  
     La boîte de dialogue **Nouvelle configuration de projet** s'affiche.  
  
4.  Dans la zone **Nom**, entrez un nom pour la nouvelle configuration.  
  
5.  Pour utiliser les propriétés d'une configuration de projet existant, choisissez une configuration dans la liste déroulante **Copier les paramètres à partir de**.  
  
6.  Pour créer en même temps une configuration de solution, cochez la case **Créer des configurations de solutions**.  
  
#### Pour renommer une configuration de projet  
  
1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.  
  
2.  Dans la colonne **Projet**, sélectionnez le projet avec la configuration de projet que vous souhaitez renommer.  
  
3.  Dans la liste déroulante **Configuration** correspondant à ce projet, choisissez **Modifier**.  
  
     La boîte de dialogue **Modifier les configurations de projet** s'affiche.  
  
4.  Sélectionnez le nom de configuration de projet que vous voulez modifier.  
  
5.  Sélectionnez **Renommer**, puis entrez un nouveau nom.  
  
## Création et modification des configurations de build de solution  
  
#### Pour créer une configuration de build de solution  
  
1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.  
  
2.  Dans la liste déroulante **Configuration de la solution active**, choisissez **Nouveau**.  
  
     La boîte de dialogue **Nouvelle configuration de solution** s'affiche.  
  
3.  Dans la zone de texte **Nom**, entrez un nom pour la nouvelle configuration.  
  
4.  Pour utiliser les propriétés d'une configuration de solution existante, choisissez une configuration dans la liste déroulante **Copier les paramètres à partir de**.  
  
5.  Pour créer en même temps plusieurs configurations de projet, activez la case à cocher **Créer des configurations de projet**.  
  
#### Pour renommer une configuration de build de solution  
  
1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.  
  
2.  Dans la liste déroulante **Configuration de la solution active**, choisissez **Modifier**.  
  
     La boîte de dialogue **Modifier les configurations de solutions** s'affiche.  
  
3.  Sélectionnez le nom de configuration de build de solution que vous voulez modifier.  
  
4.  Sélectionnez **Renommer**, puis entrez un nouveau nom.  
  
#### Pour modifier une configuration de build de solution  
  
1.  Ouvrez la boîte de dialogue **Gestionnaire de configurations**.  
  
2.  Dans la liste déroulante **Configuration de la solution active**, sélectionnez la configuration que vous souhaitez.  
  
3.  Dans le volet **Contextes des projets**, pour chaque projet, sélectionnez la **Configuration** et la **Plateforme** souhaitées, puis indiquez si vous souhaitez la **Générer** ou la **Déployer**.  
  
## Voir aussi  
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)