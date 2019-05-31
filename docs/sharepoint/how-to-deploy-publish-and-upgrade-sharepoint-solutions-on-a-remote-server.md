---
title: Déployer, publier et mettre à niveau des solutions SharePoint à distance
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8e9c46a9acaf8c70fa434514785276f9ba343d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401445"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procédure : Déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant
  En plus de déployer des solutions SharePoint sur le système local, vous pouvez publier des solutions SharePoint sandbox pour les sites distants ou des sites SharePoint locaux. Les copies de processus de publication à distance le *.wsp* fichier sur le serveur SharePoint, installe la solution, puis vous permet d’activer la solution. Vous pouvez également mettre à niveau une installation distante de la solution SharePoint une fois que les modifications sont apportées à ce dernier.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Pour publier une solution bac à sable SharePoint sur un serveur SharePoint distant

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le projet SharePoint sandbox que vous souhaitez publier, puis choisissez **publier**.

2. Dans le **publier** boîte de dialogue, sélectionnez le **publier sur le SharePoint Site** case d’option, puis entrez une URL pour un site de publication en ligne, telles que : `https://mytestsite.sharepoint.microsoftonline.com`.

3. Choisissez le **ouvrir la page Galerie de solutions dans le navigateur après la publication** case d’option pour afficher la liste des solutions dans le **galerie de solutions** page après la publication.

4. Choisissez le **publier** bouton.

5. Connectez-vous au serveur distant si l’authentification utilisateur est requise.

     La progression de la publication s’affiche dans Visual Studio **sortie** fenêtre. Lorsque le processus est terminé, la solution ( *.wsp*) fichier est installé sur le serveur SharePoint distant. Cependant, il doit toujours être activé avant de pouvoir être utilisé dans SharePoint.

6. Sur le **galerie de solutions** page, sélectionnez l’application SharePoint, sur le ruban, puis le **activer** bouton.

7. Dans le **activer la Solution** boîte de dialogue, dans le ruban, choisissez le **activer** bouton à nouveau.

     Le **état** colonne sur le **galerie de solutions** page indique que l’application est active.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Pour mettre à niveau une solution bac à SharePoint sur un serveur SharePoint distant
 Si une solution bac à sable SharePoint est déjà publiée sur un serveur distant, le processus suivant vous permet de mettre à niveau une fois que vous apportez des modifications à l’application dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. Renommer le package SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour ce faire, dans **l’Explorateur de solutions** ouvrir le package. Il apparaît dans le **Explorateur de Package**.

2. Dans **Explorateur de Package**, dans le **nom** , changez le nom du package à un nom unique.

3. Enregistrez le projet.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **publier**.

5. Dans le **publier** boîte de dialogue, sélectionnez le **publier sur le SharePoint Site** case d’option et puis, si l’URL pour le serveur distant dans lequel la solution est enregistrée est manquant, entrez-la.

6. Choisissez le **ouvrir la page Galerie de solutions dans le navigateur après la publication** case d’option pour afficher la liste des solutions dans le **galerie de solutions** page après la publication.

7. Choisissez le **publier** bouton.

8. Connectez-vous au serveur distant si l’authentification utilisateur est requise.

     Si vous connecté au serveur distant récemment, l’authentification n’est peut-être pas nécessaire.

     Si l’ancienne version de l’application qui a le même nom existe toujours sur le serveur SharePoint, vous obtiendrez une erreur un package portant le même nom existe déjà sur le serveur SharePoint. Vous devez renommer le package à un nom unique avant la publication.

9. Choisissez la nouvelle application dans SharePoint, puis, dans le ruban, le **mise à niveau** bouton.

10. Dans le **mettre à niveau une Solution** boîte de dialogue, dans le ruban, choisissez le **mise à niveau** bouton à nouveau. Le **état** colonne sur le **galerie de solutions** page doit maintenant indiquer que l’application est active.

     L’ancienne version de la solution est désactivée, la nouvelle version de la solution est mis à niveau avec les données conservées à partir de l’ancienne solution et la nouvelle solution est activée dans SharePoint.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Déployer et publier une solution SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Créer des packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Guide pratique pour Personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Guide pratique pour Ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
