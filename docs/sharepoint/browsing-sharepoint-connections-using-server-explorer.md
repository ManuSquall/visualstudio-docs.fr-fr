---
title: Exploration des connexions SharePoint à l’aide de Explorateur de serveurs | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016350"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Parcourir les connexions SharePoint à l’aide de Explorateur de serveurs
  Vous pouvez maintenant parcourir les connexions SharePoint locales dans **Explorateur de serveurs**. À l’aide de cette technique, vous pouvez naviguer dans les composants d’un site SharePoint sur votre système. Les composants de site SharePoint, tels que les définitions de listes et les types de contenu, apparaissent dans un nœud nommé **Connexions SharePoint** dans l’arborescence de **Explorateur de serveurs**. Pour afficher **Explorateur de serveurs**, dans la barre de menus, choisissez **Afficher**les  >  **Explorateur de serveurs**. Outre l’affichage des composants de site SharePoint, vous pouvez supprimer des éléments, afficher leurs propriétés ou actualiser l’arborescence à l’aide des commandes du menu contextuel.

> [!IMPORTANT]
> Pour parcourir un site SharePoint, vous devez être administrateur de la collection de sites SharePoint et vous devez exécuter Visual Studio en tant qu’administrateur de l’ordinateur local. Dans le cas contraire, le site s’affiche dans **Explorateur de serveurs**, mais vous ne pouvez pas développer son nœud. Pour vérifier si vous êtes un administrateur de la collection de sites, ouvrez le site dans un navigateur Web, ouvrez le menu **actions du site** , choisissez **autorisations du site**, puis, dans la page **autorisations : site d’équipe** , choisissez la commande administrateurs de la collection de **sites** dans le groupe **gérer** sur le ruban. Votre nom apparaîtra dans la zone de texte si vous êtes administrateur de collection de sites. Si la commande administrateurs de la **collection de sites** n’apparaît pas dans le groupe gérer sur le ruban, vous n’êtes pas administrateur de la collection de sites et vous devez obtenir les autorisations appropriées auprès de l’administrateur du site.

## <a name="server-explorer-nodes"></a>Nœuds de Explorateur de serveurs
 Chaque composant d’un site SharePoint est représenté par un nœud dans l’arborescence **Explorateur de serveurs** sous **Connexions SharePoint**. Par exemple, les sites SharePoint par défaut incluent un type de contenu appelé discussion, qui représente un type de discussion qui s’affiche dans la page **discussions** du site SharePoint. Le type de contenu discussion contient plusieurs champs. Pour afficher ces champs dans **Explorateur de serveurs**, développez le nœud **ContentTypes** , puis le nœud **discussion** . Il s’agit de plusieurs nœuds de champ, tels que corps, sujet de discussion et titre.

## <a name="node-shortcut-menu-commands"></a>Commandes du menu contextuel du nœud
 Chaque nœud possède un menu contextuel auquel vous accédez en cliquant avec le bouton droit sur le nœud ou en le sélectionnant, puis en choisissant les touches **MAJ** + **F10** . Les commandes de nœud peuvent inclure les éléments suivants :

|Nom de la commande|Description|
|------------------|-----------------|
|Actualiser|Met à jour l’arborescence pour refléter toutes les modifications qui ont pu se produire depuis la dernière affichage du nœud.|
|DELETE|Supprime le nœud sélectionné de l’arborescence. **Remarque :**  Cette commande est activée uniquement sur les connexions SharePoint listées sous le nœud **Connexions SharePoint** .|
|Propriétés|Affiche les propriétés disponibles pour le nœud sélectionné dans la fenêtre **Propriétés** . Les propriétés sont en lecture seule, et tous les nœuds n’ont pas de propriétés associées.|
|Ajouter une connexion|Vous permet de spécifier un site SharePoint que vous souhaitez parcourir. Disponible sur le nœud **Connexions SharePoint** et les nœuds de sous-site.|
|Afficher dans le navigateur|Affiche la liste sélectionnée dans le navigateur Web. Cette commande est disponible sur certaines listes sous le nœud **listes** qui est contenu dans les **listes et les bibliothèques**.|

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Procédure : ajouter ou supprimer des connexions SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Décrit les étapes requises pour ajouter un nouveau site SharePoint au nœud **Connexions SharePoint** dans **Explorateur de serveurs**.|

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
