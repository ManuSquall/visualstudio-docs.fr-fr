---
title: 'Procédure : Ajouter ou supprimer des connexions SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3c094ad703727903e7109d6a748b8383e4cad7d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435483"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procédure : Ajouter ou supprimer des connexions SharePoint
  Explorateur de serveurs vous permet de parcourir des sites SharePoint, ainsi que des connexions de données. Toutefois, avant de pouvoir parcourir le contenu d’un site SharePoint vous devez l’ajouter à la **connexions SharePoint** nœud.

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Pour ajouter un site SharePoint au nœud Connexions SharePoint

1. Dans la barre de menus, choisissez **vue**, **Explorateur de serveurs**.

2. Dans **Explorateur de serveurs**, choisissez le **connexions SharePoint** nœud, puis, dans la barre de menus, choisissez **outils** > **ajouter SharePoint Connexion**.

3. Dans le **ajouter une connexion SharePoint** , entrez la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pour le site SharePoint (par exemple, http://testserver/sites/unittests).

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Pour supprimer un site SharePoint à partir du nœud Connexions SharePoint

1. Dans la barre de menus, choisissez **vue**, **Explorateur de serveurs** pour ouvrir **Explorateur de serveurs**.

2. Développez le **connexions SharePoint** nœud pour afficher le site SharePoint que vous souhaitez supprimer de **Explorateur de serveurs**.

3. Choisissez le site, puis, dans la barre de menus, **modifier** > **supprimer**.

    > [!NOTE]
    > Cette étape ne supprime pas le site sous-jacente ; elle supprime uniquement la connexion à partir de **Explorateur de serveurs**.

## <a name="see-also"></a>Voir aussi
- [Parcourir les connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
