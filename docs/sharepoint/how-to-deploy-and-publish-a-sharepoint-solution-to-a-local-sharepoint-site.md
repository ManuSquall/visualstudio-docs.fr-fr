---
title: "Comment&#160;: d&#233;ployer et publier une solution SharePoint sur le site SharePoint local"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déployer (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, déployer"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;ployer et publier une solution SharePoint sur le site SharePoint local
  Vous pouvez déployer ou publier des solutions SharePoint sur le serveur local SharePoint depuis votre ordinateur de développement.  Le processus de déploiement copie le fichier .wsp sur le serveur SharePoint, installe la solution, puis active les fonctionnalités.  Le processus de publication copie uniquement le fichier .wsp vers le serveur SharePoint l'installe.  Vous devez manuellement l'activer pour l'activer dans SharePoint.  
  
## Pour déployer une solution SharePoint sur le serveur SharePoint local  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le projet à déployer.  
  
2.  Dans la barre de menus, choisissez **Générer**, puis **Déployer la solution**.  
  
     Cela a pour effet de créer et d'installer le fichier .wsp sur le serveur SharePoint local  et d'activer les fonctionnalités.  
  
## Pour publier une solution SharePoint sur un serveur SharePoint local  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet SharePoint que vous souhaitez publier et choisissez **Publier**.  
  
2.  Dans la boîte de dialogue **Publier**, sélectionnez la case d'option **Publier dans le système de fichiers**.  
  
3.  Dans la zone de texte **Emplacement cible**, entrez le chemin d'accès local, puis cliquez sur le bouton **Publier**.  
  
     La progression de la publication s'affiche dans la fenêtre de Visual Studio **Sortie**.  Lorsque le processus est terminé, le fichier de solution \(.wsp\) est installé sur le serveur local SharePoint.  Toutefois, il doit être activé pour être utilisé dans SharePoint.  Si le fichier solution existe déjà, une erreur se produit et vous demande si vous souhaitez remplacer un fichier existant.  Pour plus d'informations sur la mise à niveau du package, consultez la section sur les packages distants de mise à niveau dans [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Voir aussi  
 [Comment : déployer, publier et mettre à niveau des solutions SharePoint sur un serveur distant](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Création de packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l'aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  