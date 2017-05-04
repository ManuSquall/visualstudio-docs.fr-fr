---
title: "Comment&#160;: ajouter un param&#232;tre &#224; une m&#233;thode | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), ajouter une méthode à un paramètre"
  - "BDC (développement SharePoint dans Visual Studio), paramètres de méthodes"
  - "BDC (développement SharePoint dans Visual Studio), paramètre"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter une méthode à un paramètre"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), paramètres de méthodes"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), paramètre"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: ajouter un param&#232;tre &#224; une m&#233;thode
  Vous pouvez utiliser un paramètre pour transmettre des informations à l'intérieur d'une méthode ou retourner des informations à partir d'une méthode.  Toutes les méthodes doivent avoir au moins un paramètre.  Pour plus d'informations sur la conception d'un paramètre qui prenne en charge le type de méthode que vous souhaitez créer, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Lorsque vous ajoutez un paramètre à une méthode, Visual Studio ajoute l'élément `<Parameter>` au code XML du fichier de modèle dans votre projet.  Pour plus d'informations sur les attributs d'un élément de `<Parameter>`, consultez [Paramètre](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### Pour ajouter un paramètre à une méthode  
  
1.  Ajoutez une méthode à une entité.  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre **Détails de méthode BDC** s'ouvre.  Pour plus d'informations, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la fenêtre **Détails de méthode BDC**, développez le nœud de la méthode, puis développez le nœud **Paramètres**.  
  
4.  Dans la liste **Ajouter un paramètre**, choisissez **Créer un paramètre**.  
  
     Un nouveau paramètre s'affiche sous le nœud **Paramètres**.  
  
5.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
6.  Dans la fenêtre **Propriétés**, affectez à la propriété **Name** un nom représentatif.  Par exemple, si la méthode retourne des clients, vous pouvez la nommer ObtenirClients.  
  
7.  Dans la fenêtre **Détails de méthode BDC**, ouvrez la liste qui s'affiche pour indiquer la direction du paramètre, puis cliquez sur **In**, **InOut**, **Out** ou **Retour**.  
  
     Pour plus d'informations sur la direction à choisir pour la méthode de type que vous créez, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modifiez le descripteur de type du paramètre.  Pour plus d'informations, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Voir aussi  
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  