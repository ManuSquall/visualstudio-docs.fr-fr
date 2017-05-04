---
title: "Comment&#160;: d&#233;finir une instance de m&#233;thode | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), méthode"
  - "BDC (développement SharePoint dans Visual Studio), instance de méthode"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), méthode"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), instance de méthode"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir une instance de m&#233;thode
  Vous devez définir au moins une instance de méthode pour chaque méthode dans votre modèle.  
  
 Vous pouvez ajouter une instance de méthode à l'aide de la fenêtre **Détails de méthode BDC**.  Lorsque vous ajoutez l'instance de méthode, Visual Studio ajoute un élément `<MethodInstance>` au code XML du fichier de modèle dans votre projet.  Pour plus d'informations sur les attributs d'un élément de `<MethodInstance>`, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### Pour définir une instance de méthode  
  
1.  Dans la fenêtre **Détails de méthode BDC**, développez le nœud d'une méthode, puis développez le nœud **Instances**.  
  
2.  Dans la liste **Ajouter une instance de méthode**, cliquez sur **Créer une instance de recherche**.  
  
     Une nouvelle instance de méthode s'affiche sous le nœud **Instances**.  
  
3.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
4.  Dans la fenêtre **Propriétés**, définissez les propriétés de l'instance de méthode.  Pour plus d'informations sur chaque propriété, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## Voir aussi  
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  