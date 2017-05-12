---
title: "Comment&#160;: ajouter et supprimer des assemblys suppl&#233;mentaires"
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
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, packages"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: ajouter et supprimer des assemblys suppl&#233;mentaires
  Si un package SharePoint dépend d'autres assemblys pour les fonctionnalités ou les données, vous pouvez ajouter ces assemblys à votre package de solution \(.wsp\).  Le serveur SharePoint pourra ainsi s'assurer que les assemblys personnalisés sont installés avec un package.  
  
 Vous avez également la possibilité d'ajouter ou de modifier les contrôles sécurisés et les fichiers de ressources de classe associés aux assemblys.  
  
## Ajout d'assemblys, de contrôles sécurisés et de ressources de classe supplémentaires  
 Vous pouvez ajouter des assemblys supplémentaires au package de solution SharePoint.  Les assemblys supplémentaires d'une solution bac à sable \(sandbox\) sont déployés dans le Global Assembly Cache, mais les éléments de projet SharePoint d'une solution bac à sable \(sandbox\) sont ajoutés à la base de données de contenu.  Il est possible, en outre, d'ajouter des contrôles sécurisés et des ressources de classe à ces assemblys supplémentaires.  Pour plus d'informations sur les contrôles sécurisés, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ou « créer une entrée SafeControl » in [WebParts de déploiement dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### Pour ajouter un assembly existant  
  
1.  Ouvrez le **Concepteur de packages**.  Pour plus d'informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Sélectionnez l'onglet **Avancé**.  
  
3.  Cliquez sur le bouton **Ajouter**, puis choisissez **Ajouter un assembly existant** dans la liste.  
  
     La boîte de dialogue **Ajouter un assembly existant** s'affiche.  
  
4.  Choisissez le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\), puis choisissez l'assembly que vous avez l'intention d'ajouter.  Nous vous recommandons d'utiliser un chemin d'accès relatif à l'assembly sélectionné à des fins de portabilité.  
  
5.  Pour la **cible de déploiement**, cliquez sur le bouton d'option **GlobalAssemblyCache** afin de déployer l'assembly dans le Global Assembly Cache ou cliquez sur le boutton d'option **WebApplication** pour le déployer dans le dossier WebApplication sur le serveur SharePoint.  
  
#### Pour ajouter un assembly à partir d'une sortie de projet  
  
1.  Ouvrez le **Concepteur de packages**.  
  
     Pour plus d'informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Sélectionnez l'onglet **Avancé**.  
  
3.  Cliquez sur le bouton **Ajouter**, puis choisissez **Ajouter un assembly à partir de la sortie de projet** dans la liste.  
  
     La boîte de dialogue **Ajouter un assembly à partir de la sortie de projet** s'affiche.  
  
4.  Dans la liste **Projet source**, puis sélectionnez le projet source que vous souhaitez ajouter.  
  
5.  Pour la **cible de déploiement**, cliquez sur le boutton d'option **GlobalAssemblyCache** afin de déployer l'assembly dans le Global Assembly Cache ou cliquez sur le bouton d'option **WebApplication** pour le déployer dans le dossier WebApplication sur le serveur SharePoint.  
  
#### Pour ajouter un contrôle sécurisé  
  
1.  Ouvrez la boîte de dialogue **Modifier un assembly existant**.  Pour ce faire, ouvrez le Concepteur de packages, allez dans l'onglet **Avancé**, sélectionnez un assembly, puis cliquez sur **Modifier**.  
  
2.  Dans le panneau **Contrôle sécurisés**, cliquez sur le bouton **Cliquez ici pour ajouter un nouvel élément**.  
  
3.  Dans la colonne **Nom de l'assembly**, entrez le nom de l'assembly.  
  
4.  Dans la colonne **Espace de noms**, entrez le nom de l'espace de noms pour le contrôle sécurisé.  
  
5.  Dans la colonne **Nom de type**, entrez le nom du type.  
  
#### Pour ajouter une ressource de classe  
  
1.  Ouvrez la boîte de dialogue **Modifier un assembly existant**.  Pour ce faire, ouvrez le Concepteur de packages, allez dans l'onglet **Avancé**, sélectionnez un assembly, puis cliquez sur le bouton **Modifier**.  
  
2.  Dans le volet **Ressources de classe**, cliquez sur le bouton **Cliquez ici pour ajouter un nouvel élément**.  
  
3.  Dans la colonne **Nom de fichier**, cliquez sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\) et sélectionnez la ressource de classe que vous voulez ajouter.  
  
## Suppression des assemblys personnalisés  
 Vous pouvez supprimer des assemblys dans un package SharePoint ou éliminer les contrôles sécurisés et les ressources de classe d'assemblys existants.  
  
#### Pour supprimer un assembly existant  
  
1.  Ouvrez le **Concepteur de packages**.  Pour plus d'informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Sélectionnez l'onglet **Avancé**.  
  
3.  Dans le volet **Assemblys supplémentaires**, cliquez sur l'assembly personnalisé que vous voulez supprimer.  
  
4.  Choisissez le bouton **Supprimer**.  
  
#### Pour supprimer un contrôle sécurisé pour un assembly  
  
1.  Ouvrez la boîte de dialogue **Modifier un assembly existant**.  Pour ce faire, ouvrez le Concepteur de packages, allez dans l'onglet **Avancé**, sélectionnez un assembly, puis cliquez sur le bouton **Modifier**.  
  
2.  Choisissez le contrôle sécurisé que vous voulez supprimer.  
  
3.  Appuyez sur la touche SUPPR.  
  
#### Pour supprimer une ressource de classe pour un assembly  
  
1.  Ouvrez la boîte de dialogue **Modifier un assembly existant**.  Pour ce faire, ouvrez le Concepteur de packages, allez dans l'onglet **Avancé**, sélectionnez un assembly, puis cliquez sur le bouton **Modifier**.  
  
2.  Choisissez la ressource de classe que vous souhaitez supprimer.  
  
3.  Appuyez sur la touche SUPPR.  
  
## Voir aussi  
 [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/fr-fr/700a570a-e98e-4425-aadd-34c014868d43)  
  
  