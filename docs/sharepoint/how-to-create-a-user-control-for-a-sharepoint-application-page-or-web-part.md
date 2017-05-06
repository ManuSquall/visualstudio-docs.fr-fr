---
title: "Comment&#160;: cr&#233;er un contr&#244;le utilisateur pour un composant WebPart ou une page d&#39;application SharePoint"
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
  - "contrôles utilisateur (développement SharePoint dans Visual Studio), ajouter"
  - "contrôles utilisateur (développement SharePoint dans Visual Studio), créer"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er un contr&#244;le utilisateur pour un composant WebPart ou une page d&#39;application SharePoint
  Vous pouvez créer des contrôles d'utilisateur personnalisés qui fournissent des fonctionnalités personnalisées pour votre solution SharePoint, et vous pouvez réutiliser ces fonctionnalités à l'intérieur de votre projet.  Vous pouvez inclure des contrôles d'utilisateur dans dans une page de WebPart ou une page d'application, ajouter d'autres contrôles ASP.NET et d'autres contrôles SharePoint, et définir des propriétés et des méthodes pour le contrôle.  Pour plus d'informations sur les contrôles d'utilisateurs, consultez [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) et [Contrôles d'utilisateurs et contrôles de serveurs dans SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### Pour créer un contrôle utilisateur pour SharePoint  
  
1.  Ouvrez ou créez un projet SharePoint dans Visual Studio.  
  
     Consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l'**Explorateur de solutions**, sélectionnez le nœud du projet.  
  
3.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'ouvre.  
  
4.  Dans le volet **Installé**, choisissez le nœud **Office\/SharePoint**.  
  
5.  Dans la liste de modèles SharePoint, sélectionnez **Contrôle utilisateur \(solution de batterie uniquement\)**.  
  
    > [!NOTE]  
    >  Les contrôles utilisateur fonctionnent uniquement avec des solutions de batterie.  
  
6.  Dans la zone **Nom**, indiquez un nom pour le contrôle d'utilisateur, puis choisissez le bouton **Ajouter**.  
  
     Visual Studio ajoute plusieurs dossiers et fichiers à votre projet.  Pour plus d'informations sur ces fichiers, consultez [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Par défaut, le fichier du contrôle utilisateur s'affiche en mode **Source** dans le concepteur Visual Web Developer.  Dans ce mode, vous pouvez modifier le balisage XML du contrôle.  Passez à la vue **Design** si vous souhaitez concevoir visuellement le contrôle en faisant glisser des contrôles à partir de la **Boîte à outils**.  Consultez [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/fr-fr/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Si vous souhaitez gérer des événements qui se produisent dans le contrôle, ajoutez du code au fichier du code du contrôle utilisateur.  
  
     Ce fichier s'affiche dans l'**Explorateur de solutions** sous le fichier du contrôle utilisateur et porte une extension .cs ou .vb, selon le langage du projet.  
  
## Voir aussi  
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  