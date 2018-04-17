---
title: Déploiement, la publication et la mise à niveau de Packages de Solution SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: aac96c7954a52a3277b08efcd89fa24a743117be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Déploiement, publication et mise à niveau de packages de solutions SharePoint
  Après avoir développé une solution SharePoint dans Visual Studio, vous pouvez déployer le fichier de package (.wsp) sur un serveur SharePoint local ou le publier sur un serveur SharePoint local ou distant. Si vous déployez les fichiers, vous pouvez personnaliser la façon dont les fichiers de package (.wsp) sont déployées.  
  
> [!NOTE]  
>  Actuellement, seules les solutions bac à sable peuvent être publiées sur les serveurs SharePoint distantes. Pour plus d’informations, consultez [considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>Déploiement, la publication et la mise à niveau  
 *Déploiement* fait référence à la copie d’un fichier de solution SharePoint créé à partir d’un projet SharePoint dans Visual Studio à un hôte local. Dans une solution déployée, vous pouvez configurer les étapes de déploiement, telles que le recyclage du pool d’Internet Information Services (IIS), l’activation de la solution après le déploiement et ainsi de suite. Pour déployer, utiliser le **déployer** commande sur le **générer** menu. Pour plus d’informations, consultez [Comment : modifier une Configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) et [Comment : déployer et publier une SharePoint Solution à un SharePoint Site Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publication* fait référence au téléchargement d’un fichier de solution bac à sable SharePoint vers SharePoint distant site ; autrement dit, un site situé sur un autre système. Vous pouvez également publier un fichier de solution bac à sable SharePoint sur un site SharePoint local, mais que le site publié sur soit local ou distant, vous ne pouvez pas configurer ses étapes de déploiement.  
  
 *La mise à niveau* fait référence à la mise à jour d’une publication existante à distance ou localement publiée solution SharePoint. Une fois que des modifications sont apportées à la solution SharePoint dans Visual Studio, vous modifiez le nom de fichier de package de la solution, republiez la solution, puis mettre à niveau la solution une fois qu’il a été republie. Si vous republiez une solution publiée localement, vous pouvez remplacer le fichier de solution existante.  
  
## <a name="deploying-packages"></a>Déploiement de Packages  
 Vous pouvez déployer les fichiers de package sur le serveur SharePoint sur votre ordinateur de développement pour tester et déboguer. Vous pouvez également créer un fichier de package que vous pouvez installer sur un autre ordinateur en choisissant le **publier sur le système de fichiers** case d’option dans le **publier** boîte de dialogue. Le package est créé et copié vers le chemin d’accès local spécifié. Pour déployer une solution SharePoint sur le serveur local, utilisez le **déployer** commande sur le **générer** menu. Pour plus d’informations, consultez [Comment : déployer et publier une SharePoint Solution à un SharePoint Site Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Pour savoir comment déployer une définition de liste, ajouter un récepteur d’événements et utiliser le Concepteur de fonctionnalités et le Concepteur de packages, consultez [procédure pas à pas : déploiement d’une définition de liste de tâches de projet](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Personnalisation du processus de déploiement  
 Le tableau suivant montre les deux configurations de déploiement que vous pouvez utiliser lors du débogage et déployez une solution SharePoint.  
  
|Configuration de déploiement|Description|  
|------------------------------|-----------------|  
|Par défaut|La configuration de déploiement par défaut. Les étapes de déploiement suivantes sont effectuées :<br /><br /> 1.  Exécutez la commande de prédéploiement.<br />2.  Recycler le pool d’applications IIS.<br />3.  Retirer la solution.<br />4.  Ajouter la solution.<br />5.  Activez les fonctionnalités.<br />6.  Exécutez la commande de post-déploiement.<br /><br /> Lorsqu’un package est désinstallé, les étapes de retrait suivantes sont effectuées.<br /><br /> 1.  Recycler le pool d’applications IIS.<br />2.  Retirer la solution.|  
|Aucune activation|Cette configuration de déploiement exécute les mêmes étapes que la configuration par défaut, mais ignore l’étape d’activation.|  
  
 Vous pouvez créer vos propres configurations de déploiement pour terminer une seule étape ou de modifier l’ordre des étapes du processus de déploiement. Pour plus d’informations, consultez [Comment : modifier une Configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Vous pouvez également ajouter des commandes à exécuter avant et après le déploiement. Pour plus d’informations, consultez [Comment : définir des commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Publication des Packages sur un serveur Local ou distant  
 Pour publier une solution bac à sable de SharePoint sur un serveur distant, dans la barre de menus, choisissez **générer**, **publier**, puis, dans le **publier** boîte de dialogue, choisissez le **Publier sur le SharePoint Site** case d’option, fournir les URL du serveur distant, tel que **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Pour publier une solution SharePoint sur un serveur local, dans le **publier** boîte de dialogue, choisissez le **publier sur le système de fichiers** case d’option, en fournissant un chemin d’accès de système local.  
  
 Une fois une solution publie correctement dans SharePoint, la solution s’affiche dans le **galerie de solutions** où vous pouvez l’activer. Pour plus d’informations, consultez [Comment : déployer, publier et mettre à niveau des Solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>La mise à niveau les Packages publiés  
 Si vous apportez des modifications à un projet SharePoint dans Visual Studio après sa publication, le package publié doit être mis à niveau pour inclure les modifications. Pour mettre à niveau avec succès, un package doit avoir un nom unique. Si un package portant le même nom se trouve sur le site SharePoint, ce qui peut se produire lorsque vous mettez à jour une application existante - alertes d’erreur vous au nom de fichier sont en conflit et vous permet de renommer le package. Une fois la nouvelle publication, le nouveau package apparaît sur le site SharePoint et peut être mis à niveau. Un package mis à niveau la solution des mises à jour à l’aide de données à partir du package plus anciens, puis active la solution dans SharePoint. Pour plus d’informations, consultez [Comment : déployer, publier et mettre à niveau des Solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  