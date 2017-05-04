---
title: "Comment&#160;: cr&#233;er une association entre des entit&#233;s | Microsoft Docs"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), associer des types de contenu externes"
  - "BDC (développement SharePoint dans Visual Studio), associations entre des entités"
  - "BDC (développement SharePoint dans Visual Studio), créer une association"
  - "BDC (développement SharePoint dans Visual Studio), associer des entités"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), associer des types de contenu externes"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), associations entre des entités"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), créer une association"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), associer des entités"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er une association entre des entit&#233;s
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers \(BDC, Business Data Connectivity\) en créant des associations.  Visual Studio génère des méthodes qui fournissent aux consommateurs du modèle des informations sur chaque association.  Ces méthodes peuvent être consommées par des composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher des relations de données dans une interface utilisateur.  
  
 Vous pouvez créer deux types d'associations dans le concepteur BDC : des associations de clé étrangère ou des associations sans clé étrangère.  Pour plus d'informations, consultez [Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md).  
  
### Pour créer une association entre des entités  
  
1.  Sur l'onglet **BusinessDataConnectivity** de la **Boîte à outils**, choisissez l'élément **Association**.  
  
2.  Dans le concepteur BDC, choisissez l'entité source, puis l'entité de destination.  
  
     L'**Éditeur d'associations** s'affiche.  
  
3.  Si vous souhaitez créer une association de clé étrangère, activez la case à cocher **Est une association de clé étrangère**.  
  
    1.  Dans la colonne **ID source** du tableau **Mappage des identificateurs**, choisissez l'identificateur en regard de chaque descripteur de type correspondant qui figure dans la colonne **Champ**.  
  
         Par exemple, dans la colonne **ID source**, sélectionnez `ContactID` en regard du descripteur de type `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` et du descripteur de type `ReadItem.salesOrder.SalesOrder.ContactID`.  
  
4.  Si vous souhaitez créer une association sans clé étrangère, désactivez la case à cocher **Est une association de clé étrangère**.  
  
5.  Sélectionnez le bouton **OK**.  
  
6.  Dans le concepteur BDC, une ligne qui représente l'association s'affiche entre l'entité source et l'entité de destination.  
  
     Visual Studio ajoute une méthode du navigateur d'associations à la classe de service de l'entité de destination et à la classe de service de l'entité source.  Pour plus d'informations sur les méthodes de navigation d'associations, consultez [Opérations prises en charge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Dans la méthode du navigateur d'associations de l'entité source, ajoutez du code qui retourne une collection d'entités de destination.  
  
8.  Dans la méthode du navigateur d'associations de l'entité de destination, ajoutez du code qui retourne l'entité source associée.  
  
     Pour obtenir des exemples de méthodes du navigateur d'associations, consultez [Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md).  
  
## Voir aussi  
 [Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procédure pas à pas : création d'une liste externe dans SharePoint à l'aide de données métiers](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  