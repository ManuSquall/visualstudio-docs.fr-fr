---
title: 'Comment : déployer et publier une Solution SharePoint à un Site SharePoint Local | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c4f7e347f9cea3a73ab5326b42720a1b2c33529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Comment : déployer et publier une solution SharePoint sur le site SharePoint local
  Vous pouvez déployer ou publier des solutions SharePoint sur un serveur SharePoint local sur votre ordinateur de développement. Le processus de déploiement copie le fichier .wsp sur le serveur SharePoint, installe la solution, puis active les fonctionnalités. Le processus de publication seulement copie le fichier .wsp sur le serveur SharePoint et l’installe. Vous devez activer manuellement pour l’activer dans SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Pour déployer une solution SharePoint sur le serveur SharePoint local  
  
1.  Dans **l’Explorateur de solutions**, choisissez le projet que vous souhaitez déployer.  
  
2.  Dans la barre de menus, choisissez **générer**, **déployer la Solution**.  
  
     Le fichier .wsp est créé et installé sur le serveur SharePoint local. En outre, les fonctionnalités sont activées.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Pour publier une solution SharePoint sur un serveur SharePoint local  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le projet SharePoint que vous souhaitez publier, puis choisissez **publier**.  
  
2.  Dans le **publier** boîte de dialogue, choisissez le **publier sur le système de fichiers** case d’option.  
  
3.  Dans le **emplacement cible** zone de texte, entrez un chemin d’accès local, puis choisissez le **publier** bouton.  
  
     La progression de la publication s’affiche dans Visual Studio **sortie** fenêtre. Lorsque le processus est terminé, le fichier de solution (.wsp) est installé sur le serveur SharePoint local. Toutefois, il doit toujours être activée pour être utilisé dans SharePoint. Si le fichier solution existe déjà, une erreur se produit et vous demande si vous souhaitez remplacer le fichier existant. Pour plus d’informations sur le package de mise à niveau, consultez la section sur la mise à niveau de packages distants dans [Comment : déployer, publier et mettre à niveau des Solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déployer, publier et mettre à niveau des Solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Création de Packages de Solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Comment : personnaliser un Package de Solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Guide pratique pour ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  