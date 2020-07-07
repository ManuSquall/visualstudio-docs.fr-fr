---
title: Déployer, publier et mettre à niveau des solutions SharePoint à distance &
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f05f42f8aed35696b962e71a5fce86c2956b3661
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016806"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procédure : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant
  En plus de déployer des solutions SharePoint sur le système local, vous pouvez publier des solutions SharePoint bac à sable (sandbox) sur des sites distants ou des sites SharePoint locaux. Le processus de publication à distance copie le fichier *. wsp* sur le serveur SharePoint, installe la solution, puis vous permet d’activer la solution. Vous pouvez également mettre à niveau une installation de solution SharePoint à distance après y avoir apporté des modifications.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Pour publier une solution SharePoint bac à sable (sandbox) sur un serveur SharePoint distant

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet SharePoint bac à sable (sandbox) que vous souhaitez publier, puis choisissez **publier**.

2. Dans la boîte de dialogue **publier** , sélectionnez la case d’option **publier sur le site SharePoint** , puis entrez une URL pour un site de publication en ligne, par exemple : `https://mytestsite.sharepoint.microsoftonline.com` .

3. Choisissez la **page ouvrir la Galerie de solutions dans la** case d’option navigateur après la publication pour afficher la liste des solutions dans la page **Galerie de solutions** après la publication.

4. Choisissez le bouton **Publier**.

5. Connectez-vous au serveur distant si l’authentification de l’utilisateur est requise.

     La progression de la publication s’affiche dans la fenêtre **sortie** de Visual Studio. Une fois le processus terminé, le fichier de solution (*. wsp*) est installé sur le serveur SharePoint distant. Toutefois, il doit toujours être activé pour pouvoir être utilisé dans SharePoint.

6. Dans la page **Galerie de solutions** , sélectionnez l’application SharePoint, puis, dans le ruban, cliquez sur le bouton **activer** .

7. Dans la boîte de dialogue **activer la solution** , dans le ruban, cliquez à nouveau sur le bouton **activer** .

     La colonne **État** de la page **Galerie de solutions** indique que l’application est active.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Pour mettre à niveau une solution SharePoint bac à sable (sandbox) sur un serveur SharePoint distant
 Si une solution SharePoint bac à sable (sandbox) est déjà publiée sur un serveur distant, le processus suivant vous permet de la mettre à niveau une fois que vous avez apporté des modifications à l’application dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Renommez le package SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour ce faire, dans **Explorateur de solutions** Ouvrez le package. Il apparaît dans l' **Explorateur de package**.

2. Dans l' **Explorateur de package**, dans la zone **nom** , remplacez le nom du package par un nom unique.

3. Enregistrez le projet.

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **publier**.

5. Dans la boîte de dialogue **publier** , sélectionnez la case **d’option publier sur le site SharePoint** , puis, si l’URL du serveur distant où la solution est enregistrée est manquante, entrez-la.

6. Choisissez la **page ouvrir la Galerie de solutions dans la** case d’option navigateur après la publication pour afficher la liste des solutions dans la page **Galerie de solutions** après la publication.

7. Choisissez le bouton **Publier**.

8. Connectez-vous au serveur distant si l’authentification de l’utilisateur est requise.

     Si vous avez récemment ouvert une session sur le serveur distant, l’authentification n’est peut-être pas nécessaire.

     Si la version antérieure de l’application portant le même nom existe toujours sur le serveur SharePoint, vous obtiendrez un message d’erreur indiquant qu’un package portant le même nom existe déjà sur le serveur SharePoint. Vous devez renommer le package avec un nom unique avant la publication.

9. Choisissez la nouvelle application dans SharePoint, puis, dans le ruban, cliquez sur le bouton **mettre à niveau** .

10. Dans la boîte de dialogue **mettre à niveau la solution** , sur le ruban, cliquez à nouveau sur le bouton **mettre à niveau** . La colonne **État** de la page **Galerie de solutions** doit maintenant indiquer que l’application est active.

     L’ancienne version de la solution est désactivée, la nouvelle version de la solution est mise à niveau avec des données conservées à partir de l’ancienne solution, et la nouvelle solution est activée dans SharePoint.

## <a name="see-also"></a>Voir aussi
- [Comment : déployer et publier une solution SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Créer des packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
