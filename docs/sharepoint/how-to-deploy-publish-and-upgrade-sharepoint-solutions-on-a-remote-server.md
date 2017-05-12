---
title: "Comment&#160;: d&#233;ployer, publier et mettre &#224; niveau des solutions SharePoint sur un serveur distant"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déployer (développement SharePoint dans Visual Studio)"
  - "déploiement distant (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, déployer"
  - "développement SharePoint dans Visual Studio, déploiement distant"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;ployer, publier et mettre &#224; niveau des solutions SharePoint sur un serveur distant
  En plus de déployer des solutions de SharePoint au système local, vous pouvez publier des solutions sandboxed SharePoint vers des sites distants ou des sites locaux.  Le processus de publication distant copie le fichier .wsp sur le serveur SharePoint, installe la solution, puis vous permet de vérifier la solution.  Vous pouvez également mettre à niveau une installation distante de solutions SharePoint lorsque des modifications sont apportées à ce dernier.  
  
## Pour publier une solution sandboxed SharePoint sur un serveur distant SharePoint  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet SharePoint sandboxed que vous souhaitez publier et choisissez **Publier**.  
  
2.  Dans la boîte de dialogue **Publier**, sélectionnez la case d'option **Publier sur le site SharePoint**, puis entrez l'URL d'un site publication en ligne, comme par exemple : https:\/\/mytestsite.sharepoint.microsoftonline.com.  
  
3.  Sélectionnez la case d'option **Ouvrez la page dans la galerie de solutions dans le navigateur après avoir publié** pour afficher la liste des solutions dans la page **Bibliothèque des solutions**.  
  
4.  Cliquez sur le bouton **Publish**  
  
5.  Connectez\-vous au serveur distant si l'authentification utilisateur est requise.  
  
     La progression de la publication s'affiche dans la fenêtre de Visual Studio **Sortie**.  Lorsque le processus est terminé, le fichier de solution \(.wsp\) est installé sur le serveur distant SharePoint.  Toutefois, il doit être activée pour pouvoir être utilisé dans SharePoint.  
  
6.  Dans la page **Bibliothèque des solutions**, sélectionnez l'application SharePoint puis sur le ruban, sélectionnez le bouton **Activer**.  
  
7.  Dans la boîte de dialogue **Vérifiez la solution**, dans le ruban, cliquez sur le bouton **Activer** de nouveau.  
  
     La colonne **État** dans la page **Bibliothèque des solutions** indique que l'application est active.  
  
## Pour mettre à niveau une solution sandboxed SharePoint sur un serveur distant SharePoint  
 Si une solution sandboxed SharePoint est déjà publiée sur un serveur distant, le processus suivant permet d'effectuer la mise à niveau après avoir apporté des modifications sur l'application dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Renommer le package SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour cela, dans l'**Explorateur de solutions**, ouvrez le package.  Elle apparaît dans l'**Explorateur de package**.  
  
2.  Dans **Explorateur de package**, dans la zone **Nom**, remplacez le nom du package à un nom unique.  
  
3.  Enregistrez le projet.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Publier**.  
  
5.  Dans la boîte de dialogue **Publier**, sélectionnez la case d'option **Publier sur le site SharePoint**, puis, si l'URL du serveur distant où la solution est stockée est manquant, entrez\-la.  
  
6.  Sélectionnez la case d'option **Ouvrez la page dans la galerie de solutions dans le navigateur après avoir publié** pour afficher la liste des solutions dans la page **Bibliothèque des solutions**.  
  
7.  Cliquez sur le bouton **Publish**  
  
8.  Connectez\-vous au serveur distant si l'authentification utilisateur est requise.  
  
     Si vous vous connectez au serveur distant dernièrement utilisé, l'authentification peu ne pas être nécessaire.  
  
     Si l'ancienne version de l'application qui a toujours le même nom existe déjà sur le serveur SharePoint, vous obtiendrez une erreur indiquant qu'un package portant le même nom existe déjà sur le serveur SharePoint.  Vous devez renommer le package à un nom unique avant de publier.  
  
9. Choisissez une application dans SharePoint, puis, dans le ruban, cliquez sur le bouton **Mettre à niveau**.  
  
10. Dans la boîte de dialogue **Mettre à jour le solution**, dans le ruban, cliquez sur le bouton **Mettre à jour** de nouveau.  La colonne **État** dans la page **Bibliothèque des solutions** doit maintenant indiquer que l'application est active.  
  
     L'ancienne version de la solution est désactivée, la nouvelle version de la solution est mise à niveau avec des données gérées de l'ancienne solution, et la nouvelle solution est activée dans SharePoint.  
  
## Voir aussi  
 [Comment : déployer et publier une solution SharePoint sur le site SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Création de packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l'aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  