---
title: "Parcours des connexions SharePoint &#224; l&#39;aide de l&#39;Explorateur de serveurs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Connexions SharePoint (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, parcourir des sites SharePoint"
  - "développement SharePoint dans Visual Studio, Connexions SharePoint"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Parcours des connexions SharePoint &#224; l&#39;aide de l&#39;Explorateur de serveurs
  Vous pouvez maintenant rechercher les connexions SharePoint locale dans **Explorateur de serveurs**.  En utilisant cette technique, vous pouvez ainsi passer en revue les différents composants d'un site SharePoint résidant sur votre système.  Les composants d'un site SharePoint \(tels que les définitions de listes et les types de contenu\) sont présentés dans un nœud appelé **Connexions SharePoint** dans l'arborescence de la fenêtre **Explorateur de serveurs**.  Pour afficher l'**Explorateur de serveurs**, dans la barre de menu, cliquez sur **Affichage** dans le menu **Explorateur de serveurs**..  Les commandes de menu contextuel dans l'arborescence permettent non seulement d'afficher les composants du site SharePoint, mais aussi de supprimer des éléments, de connaître leurs propriétés ou d'actualiser l'arborescence.  
  
> [!IMPORTANT]  
>  Pour parcourir un site SharePoint, vous devez être administrateur de la collection de sites SharePoint et vous devez exécuter Visual Studio en tant qu'administrateur local.  Dans le cas contraire, le site s'affiche dans l' **Explorateur de serveurs**, mais vous ne pouvez pas développer son nœud.  Pour vérifier si vous êtes administrateur de la collection de sites, ouvrez le site dans un navigateur Web, ouvrez le menu **Actions de site**, choisissez **Autorisations de site**, puis, dans la page **Autorisations : Team Site**, choisissez la commande **Administrateur de collection de sites** du groupe **Gérer** sur le ruban.  Si vous êtes effectivement un administrateur de collection de sites, votre nom doit figurer dans la zone de texte.  Si la commande **Administrateur de collection de sites** n'apparaît pas dans le groupe de gestion sur le ruban, vous n'êtes pas administrateur de collection de sites, et vous devez obtenir les autorisations appropriées par l'administrateur du site.  
  
## Nœuds de l'Explorateur de serveurs  
 Chaque composant d'un site SharePoint est représenté par un nœud dans l'arborescence **Explorateur de serveurs** sous **Connexions SharePoint**.  Les sites SharePoint par défaut incluent, par exemple, un type de contenu appelé Discussion qui représente un type de discussion  affiché dans la page **Discussions** du site SharePoint.  Le type de contenu Discussion est composé de plusieurs champs.  Pour examiner ces champs dans l'**Explorateur SharePoint**, développez le nœud **Types de contenus**, puis le nœud **Discussion**.  Plusieurs nœuds de champ \(Corps, Objet de la discussion et Titre\) y figurent.  
  
## Commandes du menu contextuel des nœuds  
 Chaque nœud possède un menu contextuel que vous pouvez accéder en cliquant avec le bouton droit sur le nœud ou en appuyant sur les touches Shift\+F10.  Ces menus contextuels peuvent être composés des commandes de nœud suivantes :  
  
|Nom de la commande|Description|  
|------------------------|-----------------|  
|Actualiser|Met à jour l'arborescence afin de refléter les modifications intervenues depuis le dernier affichage du nœud.|  
|Supprimer|Supprime le nœud sélectionné dans l'arborescence. **Note:**  Elle s'applique uniquement aux connexions SharePoint répertoriées sous le nœud **Connexions SharePoint**.|  
|Propriétés|Affiche les propriétés relatives au nœud sélectionné dans la fenêtre **Propriétés**.  Il faut savoir d'une part que ces propriétés sont en lecture seule et d'autre part, que les nœuds ne sont pas tous associés à des propriétés.|  
|Ajouter une connexion|Permet de spécifier le site SharePoint que vous avez l'intention de parcourir.  Disponible sur le nœud **Connexions SharePoint** et les nœuds de sous\-site.|  
|Afficher dans le navigateur|Affiche la liste sélectionnée dans le navigateur Web.  Cette commande est disponible sur certaines listes sous le nœud **Listes** contenu dans **Listes et bibliothèques**.|  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : ajouter ou supprimer des connexions SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Décrit les différentes étapes à effectuer pour ajouter un nouveau site SharePoint au nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.|  
  
## Voir aussi  
 [Server Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  