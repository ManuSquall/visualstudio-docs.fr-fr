---
title: "Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5ea474f2439b6da519563f08ffe4ddc2f6dcef30
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>Parcours des connexions SharePoint à l'aide de l'Explorateur de serveurs
  Vous pouvez maintenant rechercher des connexions SharePoint locales dans **l’Explorateur de serveurs**. À l’aide de cette technique, vous pouvez naviguer dans les composants d’un site SharePoint sur votre système. Les composants de site SharePoint, tels que les définitions de listes et types de contenu, s’affichent dans un nœud nommé **connexions SharePoint** dans l’arborescence de **l’Explorateur de serveurs**. Pour afficher les **l’Explorateur de serveurs**, dans la barre de menus, choisissez **vue**, **l’Explorateur de serveurs**. En plus d’afficher les composants du site SharePoint, vous pouvez supprimer des éléments, afficher leurs propriétés ou actualiser l’arborescence à l’aide des commandes dans le menu contextuel.  
  
> [!IMPORTANT]  
>  Pour parcourir un site SharePoint, vous devez être un administrateur de la collection de sites SharePoint, et vous devez exécuter Visual Studio en tant qu’administrateur de l’ordinateur local. Sinon, le site s’affiche dans **l’Explorateur de serveurs**, mais vous ne pouvez pas développer son nœud. Pour vérifier si vous êtes un administrateur de la collection de sites, ouvrez le site dans un navigateur web, ouvrez le **Actions du Site** menu, choisissez **autorisations sur le Site**, puis, dans le **autorisations : équipe Site** page, choisissez la **administrateurs de Collection de sites** commande à partir de la **gérer** groupe sur le ruban. Votre nom apparaîtra dans la zone de texte si vous êtes un administrateur de collection de sites. Si le **administrateurs de Collection de sites** commande n’apparaît pas dans le groupe de gestion sur le ruban, vous n’êtes pas administrateur de la collection de sites, et vous devez obtenir les autorisations appropriées à partir de l’administrateur du site.  
  
## <a name="server-explorer-nodes"></a>Nœuds de l’Explorateur de serveurs  
 Chaque composant d’un site SharePoint est représenté par un nœud dans le **l’Explorateur de serveurs** arborescence sous **connexions SharePoint**. Par exemple, les sites SharePoint par défaut incluent un type de contenu appelé Discussion qui représente un type de discussion qui affiche dans le **Discussions** page du site SharePoint. Le type de contenu Discussion contient plusieurs champs. Pour afficher ces champs dans **l’Explorateur de serveurs**, développez le **types de contenus** nœud, puis le **Discussion** nœud. Y figurent plusieurs nœuds de champ, tels que le titre, l’objet de la Discussion et corps.  
  
## <a name="node-shortcut-menu-commands"></a>Commandes de Menu contextuel de nœud  
 Chaque nœud possède un menu contextuel auxquels vous accédez en double-cliquant sur le nœud ou en sélectionnant et en appuyant sur les touches MAJ + F10. Commandes de nœud peuvent inclure les éléments suivants :  
  
|Nom de la commande|Description|  
|------------------|-----------------|  
|Actualisation|Met à jour la vue d’arborescence pour refléter les modifications qui se sont produites depuis la dernière fois que le nœud a été affiché.|  
|Supprimer|Supprime le nœud sélectionné dans l’arborescence. **Remarque :** cette commande est activée uniquement sur des connexions SharePoint répertoriées sous le **connexions SharePoint** nœud.|  
|Propriétés|Affiche les propriétés disponibles pour le nœud sélectionné dans le **propriétés** fenêtre. Les propriétés sont en lecture seule, et pas chaque nœud possède des propriétés est associé.|  
|Ajouter une connexion|Vous permet de spécifier un site SharePoint que vous souhaitez parcourir. Disponible sur le **connexions SharePoint** nœud et les nœuds de site secondaire.|  
|Afficher dans le navigateur|Affiche la liste sélectionnée dans le navigateur Web. Cette commande est disponible sur certaines listes sous la **répertorie** nœud qui est contenue dans **listes et bibliothèques**.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour ajouter ou supprimer des connexions SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Décrit les étapes requises pour ajouter un nouveau site SharePoint pour le **connexions SharePoint** nœud **l’Explorateur de serveurs**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  