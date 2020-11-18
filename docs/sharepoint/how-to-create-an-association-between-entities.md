---
title: 'Comment : créer une association entre des entités | Microsoft Docs'
description: Définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e736e0befe8aaf9a6c090615d0c43bb3f3116dbf
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849842"
---
# <a name="how-to-create-an-association-between-entities"></a>Comment : créer une association entre des entités
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations. Visual Studio génère des méthodes qui fournissent aux consommateurs du modèle des informations sur chaque association. Ces méthodes peuvent être consommées par des composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher les relations de données dans une interface utilisateur (IU).

 Vous pouvez créer deux types d’associations dans le concepteur BDC : associations de clé étrangère et associations de clé étrangère étrangères. Pour plus d’informations, consultez [créer une association entre des entités](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Pour créer une association entre des entités

1. Sous l’onglet **BusinessDataConnectivity** de la **boîte à outils**, choisissez l’élément **Association** .

2. Dans le concepteur BDC, choisissez l’entité source, puis sélectionnez l’entité de destination.

     L' **éditeur d’associations** s’affiche.

3. Si vous souhaitez créer une association basée sur une clé étrangère, activez la case à cocher **est une association de clé étrangère** .

    1. Dans la colonne **ID source** de la table de **mappage des identificateurs** , choisissez l’identificateur en regard de chaque descripteur de type correspondant qui apparaît dans la colonne **champ** .

         Par exemple, dans la colonne **ID source** , sélectionnez en `ContactID` regard du `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descripteur de type et du `ReadItem.salesOrder.SalesOrder.ContactID` descripteur de type.

4. Si vous souhaitez créer une association clé-moins étrangère, désactivez la case à cocher **est une association de clé étrangère** .

5. Choisissez le bouton **OK**.

6. Dans le concepteur BDC, une ligne qui représente l’Association apparaît entre l’entité source et l’entité de destination.

     Visual Studio ajoute une méthode de navigateur d’associations à la classe de service de l’entité de destination et à la classe de service de l’entité source. Pour plus d’informations sur les méthodes de navigation d’association, consultez [opérations prises en charge](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. Dans la méthode du navigateur d’associations de l’entité source, ajoutez le code qui retourne une collection d’entités de destination.

8. Dans la méthode du navigateur d’associations de l’entité de destination, ajoutez le code qui retourne l’entité source associée.

     Pour obtenir des exemples de méthodes du navigateur d’association, consultez [créer une association entre des entités](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Voir aussi
- [Créer une association entre des entités](../sharepoint/creating-an-association-between-entities.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
- [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Procédure pas à pas : création d’une liste externe dans SharePoint à l’aide de données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
