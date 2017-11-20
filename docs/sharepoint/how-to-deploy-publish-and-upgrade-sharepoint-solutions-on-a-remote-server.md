---
title: "Comment : déployer, publier et mettre à niveau des Solutions SharePoint sur un serveur distant | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 115509e8ff79aafa703c429b476041d558e3167c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant
  En plus de déployer des solutions SharePoint sur le système local, vous pouvez publier les solutions bac à sable SharePoint pour les sites distants ou des sites SharePoint locaux. Le processus de publication distant copie le fichier .wsp sur le serveur SharePoint, installe la solution, puis vous permet d’activer la solution. Vous pouvez également mettre à niveau une installation à distance d’une solution SharePoint une fois que les modifications sont apportées à ce dernier.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Pour publier une solution bac à sable de SharePoint sur un serveur SharePoint distant  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le bac à sable projet SharePoint que vous souhaitez publier, puis choisissez **publier**.  
  
2.  Dans le **publier** boîte de dialogue, choisissez le **publier sur le SharePoint Site** case d’option, puis entrez une URL pour un site de publication en ligne, comme l’exemple suivant : **https:// mytestsite.SharePoint.microsoftonline.com**.  
  
3.  Choisissez le **ouvrir la page Galerie de solutions dans le navigateur après la publication** case d’option pour afficher la liste des solutions dans le **galerie de solutions** page après la publication.  
  
4.  Choisissez le **publier** bouton.  
  
5.  Connectez-vous au serveur distant si l’authentification utilisateur est requise.  
  
     La progression de la publication s’affiche dans Visual Studio **sortie** fenêtre. Lorsque le processus est terminé, le fichier de solution (.wsp) est installé sur le serveur SharePoint distant. Toutefois, elle doit toujours être activée avant de pouvoir être utilisé dans SharePoint.  
  
6.  Sur le **galerie de solutions** page, sélectionnez l’application SharePoint, dans le ruban, puis le **activer** bouton.  
  
7.  Dans le **activer une Solution** boîte de dialogue, dans le ruban, choisissez le **activer** bouton Nouveau.  
  
     Le **état** colonne sur le **galerie de solutions** page indique que l’application est active.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Pour mettre à niveau une solution bac à sable de SharePoint sur un serveur SharePoint distant  
 Si une solution bac à sable de SharePoint est déjà publiée sur un serveur distant, le processus suivant vous permet de mettre à niveau après avoir apporté des modifications à l’application dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Renommez le package SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour ce faire, dans **l’Explorateur de solutions** ouvrir le package. Il s’affiche dans le **Explorateur de Package**.  
  
2.  Dans **Explorateur de Package**, dans le **nom** , changez le nom du package à un nom unique.  
  
3.  Enregistrez le projet.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **publier**.  
  
5.  Dans le **publier** boîte de dialogue, choisissez le **publier sur le SharePoint Site** case d’option, puis, si l’URL pour le serveur distant sur lequel la solution est enregistrée est manquant, entrez-le.  
  
6.  Choisissez le **ouvrir la page Galerie de solutions dans le navigateur après la publication** case d’option pour afficher la liste des solutions dans le **galerie de solutions** page après la publication.  
  
7.  Choisissez le **publier** bouton.  
  
8.  Connectez-vous au serveur distant si l’authentification utilisateur est requise.  
  
     Si vous connecté au serveur distant récemment, l’authentification ne peut pas être requise.  
  
     Si l’ancienne version de l’application qui a le même nom existe toujours sur le serveur SharePoint, vous obtiendrez une erreur qui a un package portant le même nom existe déjà sur le serveur SharePoint. Vous devez renommer le package en un nom unique avant la publication.  
  
9. Choisissez la nouvelle application dans SharePoint, puis, dans le ruban, le **mise à niveau** bouton.  
  
10. Dans le **mettre à niveau une Solution** boîte de dialogue, dans le ruban, choisissez le **mise à niveau** bouton Nouveau. Le **état** colonne sur le **galerie de solutions** page doit indiquer maintenant que l’application est active.  
  
     L’ancienne version de la solution est désactivée, la nouvelle version de la solution est mis à niveau avec les données conservées à partir de l’ancienne solution, et la nouvelle solution est activée dans SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déployer et publier une Solution SharePoint à un Site SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Création de Packages de Solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Comment : personnaliser un Package de Solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Guide pratique pour ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  