---
title: Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 825bf975d877cd6b0844e86aabff605daa30a900
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875483"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Parcourir les connexions SharePoint à l’aide de l’Explorateur de serveurs
  Vous pouvez maintenant parcourir les connexions SharePoint locales dans **Explorateur de serveurs**. À l’aide de cette technique, vous pouvez naviguer dans les composants d’un site SharePoint sur votre système. Les composants de site SharePoint, tels que les définitions de listes et types de contenu, s’affichent dans un nœud nommé **connexions SharePoint** dans l’arborescence de **Explorateur de serveurs**. Pour afficher **Explorateur de serveurs**, dans la barre de menus, choisissez **vue** > **Explorateur de serveurs**. Outre l’affichage des composants de site SharePoint, vous pouvez supprimer des éléments, afficher leurs propriétés ou actualiser l’arborescence à l’aide des commandes dans le menu contextuel.  
  
> [!IMPORTANT]  
>  Pour parcourir un site SharePoint, vous devez être un administrateur de la collection de sites SharePoint, et vous devez exécuter Visual Studio en tant qu’administrateur de l’ordinateur local. Sinon, le site s’affiche dans **Explorateur de serveurs**, mais vous ne pouvez pas développer son nœud. Pour vérifier si vous êtes un administrateur de la collection de sites, ouvrez le site dans un navigateur web, ouvrez le **Actions du Site** menu, choisissez **autorisations sur le Site**, puis, dans le **autorisations : Site d’équipe** page, choisissez le **administrateurs de Collection de sites** commande à partir de la **gérer** groupe sur le ruban. Votre nom apparaîtra dans la zone de texte si vous êtes un administrateur de collection de sites. Si le **administrateurs de Collection de sites** commande n’apparaît pas dans le groupe de gestion sur le ruban, vous n’êtes pas administrateur de la collection de sites, et vous devez obtenir les autorisations appropriées à partir de l’administrateur du site.  
  
## <a name="server-explorer-nodes"></a>Nœuds de l’Explorateur de serveurs
 Chaque composant d’un site SharePoint est représenté par un nœud dans le **Explorateur de serveurs** arborescence sous **connexions SharePoint**. Par exemple, les sites SharePoint par défaut incluent un type de contenu appelé Discussion qui représente un type de discussion qui affiche dans le **Discussions** page du site SharePoint. Le type de contenu Discussion contient plusieurs champs. Pour afficher ces champs dans **Explorateur de serveurs**, développez le **ContentTypes** nœud, puis le **Discussion** nœud. Y figurent plusieurs nœuds de champ, tels que le titre, l’objet de la Discussion et corps.  
  
## <a name="node-shortcut-menu-commands"></a>Commandes du menu contextuel de nœud
 Chaque nœud possède un menu contextuel auxquels vous accédez en double-cliquant sur le nœud ou sélectionnez-le, puis en choisissant le **MAJ**+**F10** clés. Commandes de nœud peuvent être les suivantes :  
  
|Nom de la commande|Description|  
|------------------|-----------------|  
|Actualisation|Met à jour de l’arborescence pour refléter les modifications qui se sont produites depuis la dernière fois que le nœud a été affiché.|  
|Supprimer|Supprime le nœud sélectionné dans l’arborescence. **Remarque :**  Cette commande est activée uniquement sur des connexions SharePoint répertoriées sous le **connexions SharePoint** nœud.|  
|Properties|Affiche les propriétés disponibles pour le nœud sélectionné dans le **propriétés** fenêtre. Les propriétés sont en lecture seule, et pas chaque nœud possède des propriétés est associé.|  
|Ajouter une connexion|Vous permet de spécifier un site SharePoint que vous souhaitez parcourir. Disponible sur le **connexions SharePoint** nœud et les nœuds de sous-site.|  
|Afficher dans le navigateur|Affiche la liste sélectionnée dans le navigateur Web. Cette commande est disponible sur certaines listes sous le **répertorie** nœud qui est contenue dans **listes et bibliothèques**.|  
  
## <a name="related-topics"></a>Rubriques connexes
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour Ajouter ou supprimer des connexions SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Décrit les étapes requises pour l’ajout d’un nouveau site SharePoint pour le **connexions SharePoint** nœud **Explorateur de serveurs**.|  
  
## <a name="see-also"></a>Voir aussi
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
