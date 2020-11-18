---
title: Création d’une association entre des entités | Microsoft Docs
description: Créer une association entre des entités dans votre modèle de connectivité de données métiers (BDC). En savoir plus sur les méthodes d’association et les types d’associations.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: 6a5decf8ad803bea8b1d64c79410c319dbef0be9
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850544"
---
# <a name="create-an-association-between-entities"></a>Créer une association entre des entités
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations. Visual Studio génère des méthodes qui fournissent aux consommateurs du modèle des informations sur chaque association. Ces méthodes peuvent être consommées par des composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher les relations de données dans une interface utilisateur (IU).

## <a name="create-an-association"></a>Créer une association
 Créez une association en choisissant le contrôle d' **Association** dans la **boîte à outils** de Visual Studio, en choisissant la première entité (appelée entité source), puis la deuxième entité (appelée entité de destination). Vous pouvez définir les détails de l’Association dans l' **éditeur d’associations**. Pour plus d’informations, consultez [procédure : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Méthodes d’association
 Les applications telles que les WebParts de données métier SharePoint utilisent des associations en appelant des méthodes dans la classe de service d’une entité. Vous pouvez ajouter des méthodes à la classe de service d’une entité en les sélectionnant dans l' **éditeur d’associations**.

 Par défaut, l' **éditeur d’associations** ajoute une méthode de navigation d’association aux entités source et de destination. Une méthode de navigation d’association dans l’entité source permet aux consommateurs de récupérer une liste d’entités de destination. Une méthode de navigation d’association dans l’entité de destination permet aux consommateurs de récupérer l’entité source qui est associée à une entité de destination.

 Vous devez ajouter le code à chacune de ces méthodes pour retourner les informations appropriées. Vous pouvez également ajouter d’autres types de méthodes pour prendre en charge des scénarios plus avancés. Pour plus d’informations sur chacune de ces méthodes, consultez [opérations prises en charge](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Types d’associations
 Vous pouvez créer deux types d’associations dans le concepteur BDC : associations de clé étrangère et associations de clé étrangère étrangères.

### <a name="foreign-key-based-association"></a>Association basée sur une clé étrangère
 Vous pouvez créer une association basée sur une clé étrangère en associant un identificateur de l’entité source aux descripteurs de type définis dans l’entité de destination. Cette relation permet aux consommateurs du modèle de fournir une interface utilisateur améliorée pour leurs utilisateurs. Par exemple, un formulaire dans Outlook qui permet à un utilisateur de créer une commande client qui peut afficher des clients dans une liste déroulante ; ou une liste de commandes dans SharePoint qui permet aux utilisateurs d’ouvrir une page de profil pour un client.

 Pour créer une association de clé étrangère, associez les identificateurs et les descripteurs de type qui partagent le même nom et le même type. Par exemple, vous pouvez créer une association de clé étrangère entre une `Contact` entité et une `SalesOrder` entité. L' `SalesOrder` entité retourne un `ContactID` descripteur de type dans le cadre du paramètre de retour de la recherche ou de méthodes de recherche spécifiques. Les deux descripteurs de type s’affichent dans l' **éditeur d’associations**. Pour créer une relation de clé étrangère entre l' `Contact` entité et l' `SalesOrder` entité, choisissez l' `ContactID` identificateur en regard de chacun de ces champs.

 Ajoutez du code à la méthode du navigateur d’associations de l’entité source qui retourne une collection d’entités de destination. L’exemple suivant retourne les commandes client pour un contact.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Ajoutez du code à la méthode du navigateur d’associations de l’entité de destination qui retourne une entité source. L’exemple suivant retourne le contact associé à la commande client.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Association de clé étrangère étrangère
 Vous pouvez créer une association sans mapper d’identificateurs aux descripteurs de type de champ. Créez ce type d’association lorsque l’entité source n’a pas de relation directe avec l’entité de destination. Par exemple, une `SalesOrderDetail` table n’a pas de clé étrangère qui est mappée à une clé primaire dans une `Contact` table.

 Si vous souhaitez afficher des informations dans la `SalesOrderDetail` table qui se réfère à un `Contact` , vous pouvez créer une association de clé étrangère étrangère entre l' `Contact` entité et l' `SalesOrderDetail` entité.

 Dans la méthode de navigation d’association de l' `Contact` entité, retournez les `SalesOrderDetail` entités en joignant des tables ou en appelant une procédure stockée.

 L’exemple suivant retourne les détails de toutes les commandes en joignant les tables.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 Dans la méthode de navigation d’association de l' `SalesOrderDetail` entité, retournez le associé `Contact` . l’exemple ci-dessous illustre ce cas de figure.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>Voir aussi
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Comment : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md)
