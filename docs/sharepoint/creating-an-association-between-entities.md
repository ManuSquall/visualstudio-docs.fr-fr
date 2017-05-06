---
title: "Cr&#233;ation d&#39;une association entre des entit&#233;s"
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
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
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
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Cr&#233;ation d&#39;une association entre des entit&#233;s
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers \(BDC, Business Data Connectivity\) en créant des associations.  Visual Studio génère des méthodes qui fournissent aux consommateurs du modèle des informations sur chaque association.  These methods can be consumed by SharePoint web parts, lists, or custom applications to display data relationships in a user interface \(UI\).  
  
## Création d'une association  
 Create an association by choosing the **Association** control in the Visual Studio **Toolbox**, choosing the first entity \(called the source entity\), and then choosing the second entity \(called the destination entity\).  Vous pouvez définir les détails de l'association dans l'**Éditeur d'associations**.  Pour plus d'informations, consultez [Comment : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## Méthodes d'association  
 Applications such as SharePoint business data web parts consume associations by calling methods in the service class of an entity.  Vous pouvez ajouter des méthodes à la classe de service d'une entité en les sélectionnant dans l'**Éditeur d'associations**.  
  
 Par défaut, l'**Éditeur d'associations** ajoute une méthode de navigateur d'associations à l'entité source et à l'entité de destination.  Dans l'entité source, une méthode de navigateur d'associations permet aux consommateurs de récupérer une liste d'entités de destination.  Dans l'entité de destination, une méthode de navigateur d'associations permet aux consommateurs de récupérer l'entité source qui est associée à une entité de destination.  
  
 Vous devez ajouter du code à chacune de ces méthodes pour retourner les informations appropriées.  Vous pouvez également ajouter d'autres types de méthodes pour prendre en charge un plus grand nombre de scénarios avancés.  For more information about each of these methods, see [Supported Operations](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## Types d'associations  
 Vous pouvez créer deux types d'associations dans le concepteur BDC : des associations de clé étrangère ou des associations sans clé étrangère.  
  
### Association de clé étrangère  
 Vous pouvez créer une association de clé étrangère en mettant un identificateur de l'entité source en relation avec des descripteurs de type définis dans l'entité de destination.  Cette relation permet aux consommateurs du modèle de fournir une interface utilisateur améliorée aux utilisateurs.  En voici deux exemples : un formulaire dans Outlook qui permet à un utilisateur de créer une commande client pouvant afficher les clients dans une liste déroulante ; ou une liste de commandes client dans SharePoint qui permet aux utilisateurs d'ouvrir la page de profil d'un client.  
  
 Pour créer une association de clé étrangère, mettez en relation des identificateurs et des descripteurs de type qui partagent le même nom et le même type.  Par exemple, vous pouvez créer une association de clé étrangère entre une entité `Contact` et une entité `SalesOrder`.  L'entité `SalesOrder` retourne un descripteur de type `ContactID` dans le cadre du paramètre de retour des méthodes de recherche ou de recherche spécifique.  Les deux descripteurs de type s'affichent dans l'**Éditeur d'associations**.  Pour créer une relation de clé étrangère entre l'entité `Contact` et l'entité `SalesOrder`, sélectionnez l'identificateur `ContactID` en regard de chacun de ces champs.  
  
 Vous pouvez ajouter du code à la méthode du navigateur d'associations de l'entité source qui retourne une collection d'entités de destination.  L'exemple suivant retourne les commandes client d'un contact.  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 Vous pouvez ajouter du code à la méthode du navigateur d'associations de l'entité de destination qui retourne une entité source.  L'exemple suivant retourne le contact qui est associé à la commande client.  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### Association sans clé étrangère  
 Vous pouvez créer une association sans mapper d'identificateurs à des descripteurs de type de champ.  Vous pouvez créer ce type d'association lorsque l'entité source n'a pas de relation directe avec l'entité de destination.  Tel est le cas lorsqu'une table `SalesOrderDetail` ne possède pas de clé étrangère qui soit mappée à une clé primaire dans une table `Contact`.  
  
 Si vous souhaitez afficher des informations dans la table `SalesOrderDetail` qui est associée à un `Contact`, vous pouvez créer une association sans clé étrangère entre l'entité `Contact` et l'entité `SalesOrderDetail`.  
  
 Dans la méthode du navigateur d'associations de l'entité `Contact`, vous pouvez retourner les entités `SalesOrderDetail` en joignant des tables ou en appelant une procédure stockée.  
  
 L'exemple suivant retourne les détails de toutes les commandes client suite à la jonction de tables.  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 Dans la méthode du navigateur d'associations de l'entité `SalesOrderDetail`, vous pouvez retourner le `Contact` associé,  C'est ce qu'illustre l'exemple suivant.  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  