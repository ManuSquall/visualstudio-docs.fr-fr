---
title: 'Procédure : ajouter ou supprimer des connexions SharePoint | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cec1389294c8baf169db055acb87619114d7d19b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014569"
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
