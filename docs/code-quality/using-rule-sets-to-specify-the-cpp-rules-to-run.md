---
title: "Utilisation des ensembles de r&#232;gles pour sp&#233;cifier les r&#232;gles C++ &#224; ex&#233;cuter | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Utilisation des ensembles de r&#232;gles pour sp&#233;cifier les r&#232;gles C++ &#224; ex&#233;cuter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] et [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], vous pouvez créer et modifier un *ensemble de règles* personnalisé pour satisfaire des besoins de projet spécifiques, associés à l'analyse du code.  Pour créer un ensemble de règles personnalisées C\+\+, le projet C\/C\+\+ doit être ouvert dans l'IDE de Visual Studio.  Vous ouvrez un ensemble de règles standard dans l'éditeur d'ensemble de règles puis ajoutez ou supprimez des règles spécifiques et modifiez éventuellement l'action qui se produit lorsque l'analyse du code détermine qu'une règle a été violée.  
  
 Pour créer un ensemble de règles personnalisé, il convient de l'enregistrer sous un nouveau nom de fichier.  L'ensemble de règles personnalisé est automatiquement assigné au projet.  
  
## Ouverture de l'éditeur d'ensemble de règles  
  
#### Pour créer une règle personnalisée à partir d'un seul ensemble de règles existant  
  
1.  Dans l'Explorateur de solutions, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans l'onglet **Propriétés**, choisissez **Analyse du code**.  
  
3.  Dans la liste déroulante **Ensemble de règles**, effectuez l'une des opérations suivantes :  
  
    -   Choisissez l'ensemble de règles que vous voulez personnaliser.  
  
     \- ou \-  
  
    -   Sélectionnez **\<Parcourir...\>** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.  
  
4.  Choisissez sur **Ouvrir** pour afficher les règles dans l'éditeur d'ensemble de règles.  
  
#### Pour modifier un ensemble de règles dans l'éditeur d'ensemble de règles  
  
-   Pour modifier le nom complet de l'ensemble de règles, dans le menu **Affichage**, choisissez sur **Fenêtre Propriétés**.  Entrez le nom complet dans la zone **Nom**.  Notez que le nom complet peut différer du nom de fichier.  
  
-   Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe.  Pour supprimer toutes les règles du groupe, désactivez la case à cocher.  
  
-   Pour ajouter une règle spécifique à l'ensemble de règles personnalisé, activez la case à cocher de la règle.  Pour supprimer la règle de l'ensemble de règles, désactivez la case à cocher.  
  
-   Pour modifier l'action entreprise lorsqu'une règle est violée dans une analyse du code, choisissez dans le champ **Action** correspondant à la règle, puis choisissez l'une des valeurs suivantes :  
  
     **Warn** \- génère un avertissement.  
  
     **Error** \- génère une erreur.  
  
     **None** \- désactive la règle.  Cette action revient à supprimer la règle de l'ensemble de règles.  
  
#### Pour grouper, filtrer ou modifier les champs dans l'éditeur d'ensemble de règles au moyen de la barre d'outils de l'éditeur  
  
-   Pour développer les règles dans tous les groupes, choisissez sur **Développer tout**.  
  
-   Pour réduire les règles dans tous les groupes, choisissez sur **Réduire tout.**  
  
-   Pour modifier le champ selon lequel les règles sont groupées, choisissez le champ dans la liste **Grouper par**.  Pour afficher les règles sans les grouper, choisissez **\<Aucun\>**.  
  
-   Pour ajouter ou supprimer des champs dans les colonnes de règle, choisissez **Options de colonne**.  
  
-   Pour masquer des règles qui ne s'appliquent pas à la solution actuelle, choisissez **Masquer les règles qui ne s'appliquent pas à la solution actuelle**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action Erreur, choisissez **Afficher les règles qui peuvent générer des erreurs d'analyse du code**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action Avertissement, choisissez **Afficher les règles qui peuvent générer des avertissements d'analyse du code**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action **Aucune**, choisissez **Afficher les règles qui ne sont pas activées**.  
  
-   Pour ajouter ou supprimer des ensembles de règles Microsoft par défaut dans l'ensemble de règles actuel, choisissez **Ajouter ou supprimer les ensembles de règles enfants**.