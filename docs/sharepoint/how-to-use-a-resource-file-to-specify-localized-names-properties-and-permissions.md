---
title: "Comment&#160;: utiliser un fichier de ressources pour sp&#233;cifier des noms localis&#233;s, propri&#233;t&#233;s et autorisations | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), localiser des chaînes"
  - "BDC (développement SharePoint dans Visual Studio), propriétés"
  - "BDC (développement SharePoint dans Visual Studio), fichier de ressources"
  - "BDC (développement SharePoint dans Visual Studio), chaînes de ressources"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), localiser des chaînes"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), propriétés"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), fichier de ressources"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), chaînes de ressources"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: utiliser un fichier de ressources pour sp&#233;cifier des noms localis&#233;s, propri&#233;t&#233;s et autorisations
  À l'aide d'un fichier de ressources, vous pouvez spécifier des noms localisés, définir des propriétés et appliquer les permissions aux objets définis dans un modèle de connectivité des données d'entreprise \(BDC\).  Pour spécifier ces informations, ajoutez un élément **Ressource de connectivité de données métiers** à un projet qui contient un élément **Modèle de connectivité de données métiers**.  Puis vous pouvez spécifier des noms, des propriétés et des autorisations en modifiant le code XML du fichier de ressources.  
  
### Pour ajouter un fichier de ressources BDC à un projet SharePoint  
  
1.  Dans l'**Explorateur de solutions**, développez le dossier du projet SharePoint, puis sélectionnez le dossier qui contient le modèle BDC.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
3.  Développez le nœud **SharePoint**, puis sélectionnez le nœud **2010**.  
  
4.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez l'élément **Ressource de connectivité de données métiers**.  
  
5.  Dans la zone **Nom**, spécifiez un nom au fichier de ressources et cliquez sur **Ajouter**.  
  
     Un fichier de ressources qui porte l'extension .bdcr est ajouté au projet et est ouvert afin d'être édité.  
  
6.  Ajoutez du code XML pour définir les noms localisés, les propriétés et les autorisations que vous souhaitez appliquer au modèle BDC.  
  
     Pour plus d'informations sur la façon de définir ces éléments, consultez [Modèle et fichiers de ressources](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## Voir aussi  
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  