---
title: 'Procédure : ajouter ou supprimer des connexions SharePoint | Microsoft Docs'
description: Ajoutez ou supprimez des connexions SharePoint à l’aide du nœud Connexions SharePoint dans la fenêtre Explorateur de serveurs de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923446"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procédure : ajouter ou supprimer des connexions SharePoint
  Explorateur de serveurs vous permet de parcourir les sites SharePoint ainsi que les connexions de données. Toutefois, avant de pouvoir parcourir le contenu d’un site SharePoint, vous devez l’ajouter au nœud **Connexions SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Pour ajouter un site SharePoint au nœud Connexions SharePoint

1. Dans la barre de menus, choisissez **Afficher**, **Explorateur de serveurs**.

2. Dans **Explorateur de serveurs**, choisissez le nœud **Connexions SharePoint** , puis, dans la barre de menus, choisissez **Outils**  >  **Ajouter une connexion SharePoint**.

3. Dans la zone **Ajouter une connexion SharePoint** , entrez [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pour le site SharePoint (par exemple, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Pour supprimer un site SharePoint du nœud Connexions SharePoint

1. Dans la barre de menus, choisissez **Afficher**, **Explorateur de serveurs** pour ouvrir **Explorateur de serveurs**.

2. Développez le nœud **Connexions SharePoint** pour afficher le site SharePoint que vous souhaitez supprimer de **Explorateur de serveurs**.

3. Choisissez le site, puis, dans la barre de menus, choisissez **modifier**  >  **supprimer**.

    > [!NOTE]
    > Cette étape ne supprime pas le site sous-jacent ; elle supprime uniquement la connexion de **Explorateur de serveurs**.

## <a name="see-also"></a>Voir aussi
- [Parcourir les connexions SharePoint à l’aide de Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
