---
title: "Comment : modifier une Configuration de déploiement SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 408d7801e883e85e37d721c342dba691702d77cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Comment : modifier une configuration de déploiement SharePoint
  Vous pouvez créer une configuration de déploiement ou modifier une configuration de déploiement existante. Par exemple, vous pourriez exécuter une seule étape ou modifier l’ordre des étapes du processus de déploiement. Vous voudrez créer ou modifier des configurations de déploiement, car les configurations intégrées et ajoutées par programmation ne peut pas être modifiées.  
  
## <a name="creating-a-sharepoint-deployment-configuration"></a>Création d’une Configuration de déploiement SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Pour créer une configuration de déploiement SharePoint  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, *nom_projet***propriétés**.  
  
2.  Sur le **SharePoint** , choisir le **nouveau** bouton.  
  
     Le **ajouter une nouvelle Configuration de déploiement** boîte de dialogue s’affiche.  
  
3.  Dans le **nom** texte, entrez un nom pour la configuration de déploiement.  
  
4.  Dans le **étapes de déploiement disponibles** volet, choisissez les étapes que vous souhaitez ajouter à la configuration de déploiement, cliquez sur le (**>**) bouton, puis choisissez le **OK** bouton.  
  
    > [!NOTE]  
    >  Si vous avez configuré une commande de prédéploiement ou une commande de post-déploiement, ces étapes exécutées uniquement si vous les ajoutez à une configuration de déploiement personnalisée.  
  
## <a name="changing-the-active-deployment-configuration"></a>Modification de la Configuration de déploiement Active  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Pour modifier la configuration de déploiement active  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, *nom_projet***propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **Configuration de déploiement Active** zone de liste, choisissez le nom de la configuration de déploiement que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  