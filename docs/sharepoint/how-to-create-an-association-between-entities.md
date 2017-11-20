---
title: "Comment : créer une Association entre des entités | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AssociationGroupTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92c8643a87a6226e03e8726910a459168e8b4c5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-association-between-entities"></a>Comment : créer une association entre des entités
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations. Visual Studio génère des méthodes qui fournissent des consommateurs du modèle avec des informations sur chaque association. Ces méthodes peuvent être consommées par les composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher les relations de données dans une interface utilisateur (IU).  
  
 Vous pouvez créer deux types d’associations dans le concepteur BDC : des associations basé sur des clés étrangères et les associations sans clé étrangère. Pour plus d’informations, consultez [création d’une Association entre les entités](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Pour créer une association entre des entités  
  
1.  Sur le **BusinessDataConnectivity** onglet de la **boîte à outils**, choisissez le **Association** élément.  
  
2.  Dans le concepteur BDC, choisissez l’entité source, puis l’entité de destination.  
  
     Le **Éditeur d’associations** s’affiche.  
  
3.  Si vous souhaitez créer une association de clé étrangère, sélectionnez le **est une Association de clé étrangère** case à cocher.  
  
    1.  Dans le **ID de Source de** colonne de la **mappage des identificateurs** , choisissez l’identificateur en regard de chaque descripteur de type correspondant qui s’affiche dans le **champ** colonne.  
  
         Par exemple, dans le **ID de Source de** colonne, sélectionnez `ContactID` à côté du `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descripteur de type et le `ReadItem.salesOrder.SalesOrder.ContactID` descripteur de type.  
  
4.  Si vous souhaitez créer une association sans clé étrangère, désactivez le **est une Association de clé étrangère** case à cocher.  
  
5.  Sélectionnez le bouton **OK** .  
  
6.  Dans le concepteur BDC, une ligne qui représente l’association s’affiche entre l’entité source et l’entité de destination.  
  
     Visual Studio ajoute une méthode de navigateur d’associations à la classe de service de l’entité de destination et de la classe de service de l’entité source. Pour plus d’informations sur les méthodes de Navigation de l’Association, consultez [opérations prises en charge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Dans la méthode du navigateur de l’Association de l’entité source, ajoutez le code qui retourne une collection d’entités de destination.  
  
8.  Dans la méthode du navigateur de l’Association de l’entité de destination, ajoutez le code qui retourne l’entité source associée.  
  
     Pour obtenir des exemples de méthodes du navigateur d’Association, consultez [création d’une Association entre les entités](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Association entre des entités](../sharepoint/creating-an-association-between-entities.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une Instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procédure pas à pas : création d’une liste externe dans SharePoint à l’aide de données métiers](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  