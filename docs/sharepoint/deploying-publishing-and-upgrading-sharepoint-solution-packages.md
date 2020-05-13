---
title: Déployer, publier, & mettre à niveau les paquets de solutions SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444968"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Déployer, publier et mettre à niveau les ensembles de solutions SharePoint
  Après avoir développé une solution SharePoint dans Visual Studio, vous pouvez soit déployer son fichier de paquet (.wsp) sur un serveur SharePoint local ou le publier sur un serveur SharePoint à distance ou local. Si vous déployez les fichiers, vous pouvez personnaliser le déploiement des fichiers package (.wsp).

> [!NOTE]
> Actuellement, seules les solutions sandboxed peuvent être publiées sur les serveurs SharePoint distants. Pour plus d’informations, voir [les considérations de solution Sandboxed](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Déployer, publier et mettre à niveau
 *Le déploiement* fait référence à la copie d’un fichier de solution SharePoint construit à partir d’un projet SharePoint dans Visual Studio à un hôte local. Dans une solution déployée, vous pouvez configurer les étapes de déploiement, telles que le recyclage du pool des services d’information Internet (IIS), l’activation de la solution après le déploiement, et ainsi de suite. Pour le déployer, utilisez la commande **Deploy** sur le menu **Build.** Pour plus d’informations, voir [Comment modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) et comment : Déployer et publier une solution [SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *La publication* fait référence au téléchargement d’un fichier de solution SharePoint bacé à sable à un site Partagé à distance; c’est-à-dire un site situé sur un autre système. Vous pouvez également publier un fichier de solution caillé SharePoint sur un site SharePoint local, mais que le site publié soit local ou distant, vous ne pouvez pas configurer ses étapes de déploiement.

 *La mise* à niveau fait référence à la mise à jour d’une solution SharePoint existante ou publiée localement. Une fois que des modifications sont apportées à la solution SharePoint dans Visual Studio, vous modifiez le nom de fichier de paquet de la solution, rééditer la solution, puis mettre à niveau la solution après qu’elle a réussi à rééditer. Si vous rééditer une solution publiée localement, vous pouvez remplacer le fichier de solution existant.

## <a name="deploy-packages"></a>Déployer des packages
 Vous pouvez déployer des fichiers de paquets sur le serveur SharePoint sur votre ordinateur de développement pour tester et déboguer. Vous pouvez également créer un fichier de paquet que vous pouvez installer sur un autre ordinateur en choisissant le bouton **d’option Publier pour le système de fichiers** dans la boîte de dialogue **Publish.** Le paquet est créé et copié sur le chemin de fichier local spécifié. Pour déployer une solution SharePoint sur le serveur local, utilisez la commande **Deploy** sur le menu **Build.** Pour plus d’informations, voir [Comment déployer et publier une solution SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Pour savoir comment déployer une définition de liste, ajouter un récepteur d’événement et utiliser le concepteur de fonctionnalités et le concepteur de paquets, voir [Procédure pas à pas : Déployez une définition de liste de tâches](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)de projet.

## <a name="customize-the-deployment-process"></a>Personnaliser le processus de déploiement
 Le tableau suivant affiche les deux configurations de déploiement que vous pouvez utiliser lorsque vous déboisez et déployez une solution SharePoint.

|Configuration de déploiement|Description|
|------------------------------|-----------------|
|Default|La configuration de déploiement par défaut. Les étapes de déploiement suivantes sont effectuées :<br /><br /> 1. Exécuter le commandement pré-déploiement.<br />2. Recyclez le pool d’applications IIS.<br />3. Rétracter la solution.<br />4. Ajouter la solution.<br />5. Activer les fonctionnalités.<br />6. Exécuter le commandement post-déploiement.<br /><br /> Lorsqu’un paquet n’est pas installé, les étapes de rétraction suivantes sont effectuées.<br /><br /> 1. Recyclez le pool d’applications IIS.<br />2. Rétracter la solution.|
|Pas d’activation|Cette configuration de déploiement exécute les mêmes étapes que la configuration par défaut, mais saute l’étape d’activation.|

 Vous pouvez créer vos propres configurations de déploiement pour effectuer une seule étape ou modifier l’ordre des étapes du processus de déploiement. Pour plus d’informations, voir [Comment modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Vous pouvez également ajouter des commandes pour exécuter avant et après le déploiement. Pour plus d’informations, voir [Comment définir les commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publier des paquets sur un serveur distant ou local
 Pour publier une solution SharePoint bacée à un serveur distant, sur la barre de menu, choisissez **Build**, **Publiez,** puis, dans la boîte de `https://someremoteserver.sharepoint.microsoftonline.com`dialogue **Publish,** choisissez le bouton d’option Publish to **SharePoint Site,** fournissant l’URL du serveur distant, comme .

 Pour publier une solution SharePoint sur un serveur local, dans la boîte de dialogue **Publier,** choisissez le bouton **d’option Publier pour fichier,** en fournissant une trajectoire système locale.

 Après une solution publiée avec succès sur SharePoint, la solution apparaît dans la **Galerie Solution** où vous pouvez l’activer. Pour plus d’informations, voir [Comment déployer, publier et mettre à niveau les solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Mise à niveau des forfaits publiés
 Si vous modifiez un projet SharePoint dans Visual Studio après sa publication, le paquet publié doit être mis à niveau pour inclure les modifications. Pour être mis à niveau avec succès, un paquet doit avoir un nom unique. Si un paquet du même nom se trouve sur le site SharePoint - qui peut se produire lorsque vous mise à jour d’une application existante - une erreur vous avertit du conflit de nom de fichier et vous permet de renommer le paquet. Après avoir été republié, le nouveau paquet apparaît sur le site SharePoint et peut être mis à niveau. Un paquet amélioré met à jour la solution en utilisant les données de l’ancien paquet, puis active la solution dans SharePoint. Pour plus d’informations, voir [Comment déployer, publier et mettre à niveau les solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Voir aussi
- [Emballez et déployez des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
