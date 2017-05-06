---
title: "D&#233;ploiement, publication et mise &#224; niveau de packages de solutions SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déployer (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, déployer"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# D&#233;ploiement, publication et mise &#224; niveau de packages de solutions SharePoint
  Lorsque vous développez une solution SharePoint dans Visual Studio, vous pouvez soit déployer son fichier de package \(.wsp\) sur un serveur local SharePoint soit le publier sur un serveur SharePoint distant ou local.  Si vous déployez les fichiers, vous pouvez personnaliser la façon dont les fichiers de package \(.wsp\) sont déployés.  
  
> [!NOTE]  
>  Actuellement, seules les solutions sandboxed peuvent être publiées vers des serveurs distants SharePoint.  Pour plus d'informations, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
## Le déploiement, la publication, et la mise à niveau  
 *Le déploiement* fait référence à la copie sur un hôte local d'un fichier de solution SharePoint créé à partir d'un projet SharePoint dans Visual Studio.  Dans une solution déployée, vous pouvez configurer les étapes de déploiement, telles que la réutilisation du pool Internet Information Services \(IIS\), l'activation de la solution après le déploiement, etc.  Pour déployer, utilisez la commande **Déployer** dans le menu **Générer**.  Pour plus d’informations, consultez [Comment : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) et [Comment : déployer et publier une solution SharePoint sur le site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publier* fait référence au téléchargement d'un fichier de solution sandboxed SharePoint sur un site SharePoint distant ; autrement dit, un site situé sur un autre système.  Vous pouvez également publier un fichier de solution sandboxed SharePoint sur un site SharePoint local, mais indépendamment du caractère local ou distant du site sur lequel le fichier est publié, vous ne pouvez pas configurer ses étapes de déploiement.  
  
 *La mise à jour* fait référence à la mise à jour à distance ou localement de la solution SharePoint publiée.  Une fois que toutes les modifications sont apportées à la solution SharePoint dans Visual Studio, vous devez modifiez le nom de fichier du package de la solution, republiez la solution, puis mettre à jour la solution lorsqu'elle ait été republiée correctement.  Si vous republiez une solution publiée localement, vous pouvez remplacer le fichier existant de la solution.  
  
## Déploiement de packages  
 Vous pouvez déployer vos fichiers de package sur le serveur SharePoint depuis votre ordinateur de développement en vue de procéder au test et au débogage.  Vous pouvez également créer un fichier de package que vous pouvez installer sur un autre ordinateur en cochant l'option **Publier dans le système de fichiers** dans la boîte de dialogue **Publier**.  Le package est créé et copié dans le tracé spécifié de fichiers local.  Pour déployer une solution SharePoint sur le serveur local, utilisez la commande **Déployer** dans le menu **Générer**.  Pour plus d'informations, consultez [Comment : déployer et publier une solution SharePoint sur le site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Pour apprendre à déployer une définition de liste, ajouter un récepteur d'événements et utiliser le Concepteur de fonctionnalités et le Concepteur de packages, consultez [Procédure pas à pas : déploiement d'une définition de liste de tâches de projet](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## Personnalisation du processus de déploiement  
 Le tableau suivant présente les deux configurations de déploiement que vous pouvez utiliser lors du débogage et du déploiement d'une solution SharePoint.  
  
|Configuration de déploiement|Description|  
|----------------------------------|-----------------|  
|Valeur|Configuration de déploiement par défaut.  Les étapes de déploiement suivantes sont exécutées :<br /><br /> 1.  Exécuter une commande de pré\-déploiement.<br />2.  Recycler le pool d'applications IIS.<br />3.  Retirer la solution.<br />4.  Ajouter une solution.<br />5.  Activer les fonctionnalités.<br />6.  Exécuter une commande de post\-déploiement.<br /><br /> En cas de désinstallation d'un package, les étapes de retrait suivantes sont exécutées.<br /><br /> 1.  Recycler le pool d'applications IIS.<br />2.  Retirer la solution.|  
|Aucune activation|Cette configuration de déploiement exécute les mêmes étapes que la configuration de déploiement par défaut, mais ignore l'étape d'activation.|  
  
 Vous êtes libre de définir vos propres configurations de déploiement pour effectuer une étape particulière ou de changer l'ordre des étapes dans le processus de déploiement.  Pour plus d'informations, consultez [Comment : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Vous pouvez également ajouter les commandes que vous souhaitez exécuter avant et après le déploiement.  Pour plus d'informations, consultez [Comment : définir des commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## Publier des packages vers un serveur local ou distant  
 Pour publier une solution sandboxed SharePoint sur un serveur distant, dans la barre de menus, cliquez sur **Générer**, **Publier**, puis, dans la boîte de dialogue **Publier**, cochez l'option **Publier sur le site SharePoint**, en fournissant l'URL du serveur distant, par exemple https:\/\/someremoteserver.sharepoint.microsoftonline.com.  
  
 Pour publier une solution SharePoint sur un serveur local, dans la boîte de dialogue **Publier**, cochez l'option **Publier dans le système de fichiers**, fournissez un chemin d'accès au système local.  
  
 Lorsqu'une solution publie correctement sur SharePoint, la solution apparaît dans **Bibliothèque des solutions** où vous pouvez l'activer.  Pour plus d'informations, consultez [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### Mise à jour des Packages publiés  
 Si vous apportez des modifications à un projet SharePoint dans Visual Studio après qu'il ait été publié, le package publié doit être mis à jour pour inclure les modifications.  Pour être mis à jour correctement, un package doit avoir un nom unique.  Si un package avec le même nom se trouve sur le site SharePoint – ce qui peut se produire lorsque vous mettez à jour une application existante – une erreur vous alerte du conflit de nom de fichier et vous permet de renommer le package.  Après avoir été republié, le package apparaît sur le site SharePoint et peut être mis à jour.  Un package mis à jour met à jour la solution en utilisant les données de l'ancien package, et active la solution dans SharePoint.  Pour plus d'informations, consultez [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  