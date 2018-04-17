---
title: 'Comment : modifier une Configuration de déploiement SharePoint | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97f6851b3d9aefee969851f355552373e7ecc7ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Comment : modifier une configuration de déploiement SharePoint
  Vous pouvez créer une configuration de déploiement ou modifier une configuration de déploiement existante. Par exemple, vous pourriez exécuter une seule étape ou modifier l’ordre des étapes du processus de déploiement. Vous voudrez créer ou modifier des configurations de déploiement, car les configurations intégrées et ajoutées par programmation ne peut pas être modifiées.  
  
## <a name="creating-a-sharepoint-deployment-configuration"></a>Création d’une Configuration de déploiement SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Pour créer une configuration de déploiement SharePoint  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, * NomProjet ***propriétés**.  
  
2.  Sur le **SharePoint** , choisir le **nouveau** bouton.  
  
     Le **ajouter une nouvelle Configuration de déploiement** boîte de dialogue s’affiche.  
  
3.  Dans le **nom** texte, entrez un nom pour la configuration de déploiement.  
  
4.  Dans le **étapes de déploiement disponibles** volet, choisissez les étapes que vous souhaitez ajouter à la configuration de déploiement, cliquez sur le (**>**) bouton, puis choisissez le **OK** bouton.  
  
    > [!NOTE]  
    >  Si vous avez configuré une commande de prédéploiement ou une commande de post-déploiement, ces étapes exécutées uniquement si vous les ajoutez à une configuration de déploiement personnalisée.  
  
## <a name="changing-the-active-deployment-configuration"></a>Modification de la Configuration de déploiement Active  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Pour modifier la configuration de déploiement active  
  
1.  Dans **l’Explorateur de solutions**, choisissez un projet SharePoint, puis, dans la barre de menus, choisissez **projet**, * NomProjet ***propriétés**.  
  
2.  Choisissez le **SharePoint** onglet.  
  
3.  Dans le **Configuration de déploiement Active** zone de liste, choisissez le nom de la configuration de déploiement que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  