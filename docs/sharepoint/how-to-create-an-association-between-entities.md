---
title: 'Procédure : Créer une Association entre entités | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d8558745de7539350bde4f00673c99d23cd1def
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645119"
---
# <a name="how-to-create-an-association-between-entities"></a>Procédure : Créer une association entre entités
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations. Visual Studio génère des méthodes qui fournissent des consommateurs du modèle des informations sur chaque association. Ces méthodes peuvent être consommées par les composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher les relations entre les données dans une interface utilisateur (IU).

 Vous pouvez créer deux types d’associations dans le concepteur BDC : des associations clé étrangère et des associations sans clé étrangère. Pour plus d’informations, consultez [créer une association entre entités](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Pour créer une association entre entités

1.  Sur le **BusinessDataConnectivity** onglet de la **boîte à outils**, choisissez le **Association** élément.

2.  Dans le concepteur BDC, choisissez l’entité source, puis l’entité de destination.

     Le **Éditeur d’associations** s’affiche.

3.  Si vous souhaitez créer une association de clé étrangère, sélectionnez le **est une Association de clé étrangère** case à cocher.

    1.  Dans le **ID Source** colonne de la **mappage des identificateurs** , choisissez l’identificateur en regard de chaque descripteur de type correspondant qui s’affiche dans le **champ** colonne.

         Par exemple, dans le **ID Source** colonne, sélectionnez `ContactID` regard le `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descripteur de type et le `ReadItem.salesOrder.SalesOrder.ContactID` descripteur de type.

4.  Si vous souhaitez créer une association sans clé étrangère, désactivez le **est une Association de clé étrangère** case à cocher.

5.  Sélectionnez le bouton **OK** .

6.  Dans le concepteur BDC, une ligne qui représente l’association s’affiche entre l’entité source et l’entité de destination.

     Visual Studio ajoute une méthode de navigateur d’associations à la classe de service de l’entité de destination et de la classe de service de l’entité source. Pour plus d’informations sur les méthodes de Navigation de l’Association, consultez [pris en charge les opérations](http://go.microsoft.com/fwlink/?LinkId=169286).

7.  Dans la méthode du navigateur de l’Association de l’entité source, ajoutez le code qui retourne une collection d’entités de destination.

8.  Dans la méthode du navigateur de l’Association de l’entité de destination, ajoutez le code qui retourne l’entité source associée.

     Pour obtenir des exemples de méthodes du navigateur d’Association, consultez [créer une association entre entités](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Voir aussi
- [Créer une association entre entités](../sharepoint/creating-an-association-between-entities.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Guide pratique pour Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)
- [Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
- [Guide pratique pour Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procédure pas à pas : Créer une liste externe dans SharePoint à l’aide de données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
