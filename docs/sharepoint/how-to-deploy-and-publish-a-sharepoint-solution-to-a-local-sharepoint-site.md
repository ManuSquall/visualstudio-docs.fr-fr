---
title: Déployer & publier une solution SharePoint sur un site SharePoint local
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78a837cc7145187fbc529e6e86cc27f88dd81f51
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585795"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Comment : déployer et publier une solution SharePoint sur un site SharePoint local
  Vous pouvez déployer ou publier des solutions SharePoint sur un serveur SharePoint local sur votre ordinateur de développement. Le processus de déploiement copie le fichier *. wsp* sur le serveur SharePoint, installe la solution, puis active les fonctionnalités. Le processus de publication copie uniquement le fichier *. wsp* sur le serveur SharePoint et l’installe. Vous devez l’activer manuellement pour l’activer dans SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Pour déployer une solution SharePoint sur le serveur SharePoint local

1. Dans **Explorateur de solutions**, choisissez le projet que vous souhaitez déployer.

2. Dans la barre de menus, choisissez **générer**, **déployer la solution**.

     Le fichier *. wsp* est créé et installé sur le serveur SharePoint local. En outre, les fonctionnalités sont activées.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Pour publier une solution SharePoint sur un serveur SharePoint local

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet SharePoint que vous souhaitez publier, puis choisissez **publier**.

2. Dans la boîte de dialogue **publier** , choisissez la case **d’option publier sur le système de fichiers** .

3. Dans la zone de texte **emplacement cible** , entrez un chemin d’accès local, puis cliquez sur le bouton **publier** .

     La progression de la publication s’affiche dans la fenêtre **sortie** de Visual Studio. Une fois le processus terminé, le fichier de solution (*. wsp*) est installé sur le serveur SharePoint local. Toutefois, il doit toujours être activé pour être utilisé dans SharePoint. Si le fichier solution existe déjà, une erreur se produit et vous demande si vous souhaitez remplacer le fichier existant. Pour plus d’informations sur la mise à niveau du package, consultez la section relative à la mise à niveau de packages distants dans [procédure : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Voir aussi
- [Procédure : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Créer des packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
