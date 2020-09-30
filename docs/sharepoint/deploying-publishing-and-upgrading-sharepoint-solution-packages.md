---
title: Déployer, publier, & mettre à niveau des packages de solution SharePoint
titleSuffix: ''
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
ms.openlocfilehash: 574712b870256fa7422e64a3c29ae8733f4c2251
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583877"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Déployer, publier et mettre à niveau des packages de solution SharePoint
  Une fois que vous avez développé une solution SharePoint dans Visual Studio, vous pouvez soit déployer son fichier de package (. wsp) sur un serveur SharePoint local, soit le publier sur un serveur SharePoint distant ou local. Si vous déployez les fichiers, vous pouvez personnaliser la façon dont les fichiers de package (. wsp) sont déployés.

> [!NOTE]
> Actuellement, seules les solutions bac à sable (sandbox) peuvent être publiées sur des serveurs SharePoint distants. Pour plus d’informations, consultez [Considérations sur les solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Déployer, publier et mettre à niveau
 Le *déploiement* fait référence à la copie d’un fichier de solution SharePoint créé à partir d’un projet SharePoint dans Visual Studio vers un hôte local. Dans une solution déployée, vous pouvez configurer les étapes de déploiement, telles que le recyclage du pool de Internet Information Services (IIS), l’activation de la solution après le déploiement, et ainsi de suite. Pour déployer, utilisez la commande **déployer** du menu **générer** . Pour plus d’informations, consultez [Comment : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) et [Comment : déployer et publier une solution SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 La *publication* fait référence au téléchargement d’un fichier solution SharePoint en bac à sable (sandbox) sur un site SharePoint distant. autrement dit, un site situé sur un autre système. Vous pouvez également publier un fichier de solution en mode bac à sable (sandbox) SharePoint sur un site SharePoint local, mais même si le site publié sur est local ou distant, vous ne pouvez pas configurer ses étapes de déploiement.

 La *mise à niveau* fait référence à la mise à jour d’une solution SharePoint existante, à distance ou publiée localement. Une fois les modifications apportées à la solution SharePoint dans Visual Studio, vous modifiez le nom du fichier de package de la solution, republiez la solution, puis mettez à niveau la solution une fois qu’elle a été republiée. Si vous republiez une solution publiée localement, vous pouvez remplacer le fichier solution existant.

## <a name="deploy-packages"></a>Déployer des packages
 Vous pouvez déployer des fichiers de package sur le serveur SharePoint sur votre ordinateur de développement à des fins de test et de débogage. Vous pouvez également créer un fichier de package que vous pouvez installer sur un autre ordinateur en sélectionnant la case d’option **publier sur le système de fichiers** dans la boîte de dialogue **publier** . Le package est créé et copié dans le chemin d’accès au fichier local spécifié. Pour déployer une solution SharePoint sur le serveur local, utilisez la commande **déployer** du menu **générer** . Pour plus d’informations, consultez [Comment : déployer et publier une solution SharePoint sur un site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Pour savoir comment déployer une définition de liste, ajouter un récepteur d’événements et utiliser le concepteur de fonctionnalités et le concepteur de packages, consultez [procédure pas à pas : déployer une définition de liste de tâches de projet](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personnaliser le processus de déploiement
 Le tableau suivant présente les deux configurations de déploiement que vous pouvez utiliser lorsque vous déboguez et déployez une solution SharePoint.

|Configuration du déploiement|Description|
|------------------------------|-----------------|
|Default|Configuration de déploiement par défaut. Les étapes de déploiement suivantes sont effectuées :<br /><br /> 1. Exécutez la commande de prédéploiement.<br />2. recyclez le pool d’applications IIS.<br />3. Retirez la solution.<br />4. Ajoutez la solution.<br />5. activez les fonctionnalités.<br />6. Exécutez la commande de après le déploiement.<br /><br /> Lorsqu’un package est désinstallé, les étapes de rétractation suivantes sont effectuées.<br /><br /> 1. recyclez le pool d’applications IIS.<br />2. Retirez la solution.|
|Aucune activation|Cette configuration de déploiement exécute les mêmes étapes que la configuration par défaut, mais ignore l’étape d’activation.|

 Vous pouvez créer vos propres configurations de déploiement pour effectuer une seule étape ou modifier l’ordre des étapes dans le processus de déploiement. Pour plus d’informations, consultez [Comment : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Vous pouvez également ajouter des commandes à exécuter avant et après le déploiement. Pour plus d’informations, consultez [Comment : définir des commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publier des packages sur un serveur distant ou local
 Pour publier une solution SharePoint bac à sable (sandbox) sur un serveur distant, dans la barre de menus, choisissez **générer**, **publier**, puis, dans la boîte de dialogue **publier** , choisissez la case d’option **publier sur le site SharePoint** , en fournissant l’URL du serveur distant, telle que `https://someremoteserver.sharepoint.microsoftonline.com` .

 Pour publier une solution SharePoint sur un serveur local, dans la boîte de dialogue **publier** , choisissez la case d’option **publier sur le système de fichiers** , en fournissant un chemin d’accès au système local.

 Une fois qu’une solution a été publiée avec succès sur SharePoint, la solution apparaît dans la **Galerie de solutions** où vous pouvez l’activer. Pour plus d’informations, consultez [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Mettre à niveau les packages publiés
 Si vous apportez des modifications à un projet SharePoint dans Visual Studio après sa publication, le package publié doit être mis à niveau pour inclure les modifications. Pour réussir la mise à niveau, un package doit avoir un nom unique. Si un package portant le même nom se trouve sur le site SharePoint, ce qui peut se produire lors de la mise à jour d’une application existante : une erreur vous informe du conflit de noms de fichiers et vous permet de renommer le package. Une fois la nouvelle publication effectuée, le nouveau package s’affiche sur le site SharePoint et peut être mis à niveau. Un package mis à niveau met à jour la solution à l’aide des données de l’ancien package, puis active la solution dans SharePoint. Pour plus d’informations, consultez [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
