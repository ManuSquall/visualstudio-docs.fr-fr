---
title: "Comment&#160;: cr&#233;er une page d&#39;application"
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
  - "pages d'application (développement SharePoint dans Visual Studio), ajouter"
  - "pages d'application (développement SharePoint dans Visual Studio), créer"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er une page d&#39;application
  Vous pouvez créer une page Web ASP.NET pour un ou plusieurs sites SharePoint.  Dans SharePoint, ces pages sont désignées par « pages d'application ».  À la différence d'une page de site, une page d'application contient du code qui s'exécute derrière la page.  Pour plus d'informations, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### Pour créer une page d'application  
  
1.  Ouvrez ou créez un projet SharePoint dans Visual Studio.  
  
     Pour plus d'informations, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
3.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
4.  Dans la boîte de dialogue **Ajouter un nouvel élément**, développez le noeud **SharePoint**, puis sélectionnez l'élément **2010**.  
  
5.  Dans la liste des modèles de SharePoint, choisissez **Page d'application**.  
  
6.  Dans la zone **Nom**, indiquez un nom pour la page d'application, puis choisissez le bouton **Ajouter**.  
  
     Visual Studio ajoute plusieurs dossiers et fichiers à votre projet.  Pour plus d'informations sur ces fichiers, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     Dans le mode d'affichage **Source** du concepteur de développement Visual Web, le fichier de page ASP.NET apparait.  Vous pouvez concevoir la page en ajoutant des contrôles de la **Boîte à outils** et en les plaçant sur des espaces réservés.  Pour plus d'informations, consultez [Mode Source, Concepteur de pages Web](http://msdn.microsoft.com/fr-fr/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Si vous souhaitez gérer des événements de contrôle, ajoutez du code au fichier de code de la page d'application.  
  
     Le fichier de code apparaît si vous développez le nœud du fichier de page ASP.NET et que vous disposez d'une extension .cs ou .vb, selon le langage du projet.  Pour obtenir un exemple de création de page d'application de bout en bout, consultez [Procédure pas à pas : création d'une page d'application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## Voir aussi  
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Procédure pas à pas : création d'une page d'application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  