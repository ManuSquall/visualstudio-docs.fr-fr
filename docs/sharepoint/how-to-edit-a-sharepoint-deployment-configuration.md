---
title: 'Procédure : modifier une configuration de déploiement SharePoint | Microsoft Docs'
description: Vous savez comment créer une configuration de déploiement SharePoint ou modifier une configuration de déploiement existante.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59354537f0c1f22534395da1e0ed3db3929a14a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913655"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procédure : modifier une configuration de déploiement SharePoint
  Vous pouvez créer une configuration de déploiement ou modifier une configuration de déploiement existante. Par exemple, vous pouvez exécuter une seule étape ou modifier l’ordre des étapes du processus de déploiement. Vous pouvez créer ou modifier des configurations de déploiement, car les configurations intégrées et ajoutées par programmation ne peuvent pas être modifiées.

## <a name="create-a-sharepoint-deployment-configuration"></a>Créer une configuration de déploiement SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Pour créer une configuration de déploiement SharePoint

1. Dans **Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, **Propriétés** ProjectName.

2. Sous l’onglet **SharePoint** , choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter une nouvelle configuration de déploiement** s’affiche.

3. Dans la zone de texte **nom** , entrez un nom pour la configuration de déploiement.

4. Dans le volet **étapes de déploiement disponibles** , choisissez les étapes que vous souhaitez ajouter à la configuration de déploiement, cliquez sur le **>** bouton (), puis choisissez le bouton **OK** .

    > [!NOTE]
    > Si vous avez configuré une commande de prédéploiement ou une commande de redéploiement, ces étapes s’exécutent uniquement si vous les ajoutez à une configuration de déploiement personnalisée.

## <a name="change-the-active-deployment-configuration"></a>Modifier la configuration de déploiement active

#### <a name="to-change-the-active-deployment-configuration"></a>Pour modifier la configuration de déploiement active

1. Dans **Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez   >  **\<*ProjectName*> Propriétés** du projet.

2. Choisissez l’onglet **SharePoint** .

3. Dans la zone de liste **configuration de déploiement active** , choisissez le nom de la configuration de déploiement que vous souhaitez utiliser.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
