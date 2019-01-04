---
title: Création d’une Association entre des entités | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 134b477cdc199d85c983633a2a5996d113420443
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842977"
---
# <a name="create-an-association-between-entities"></a>Créer une association entre entités
  Vous pouvez définir des relations entre des entités dans votre modèle de connectivité de données métiers (BDC) en créant des associations. Visual Studio génère des méthodes qui fournissent des consommateurs du modèle des informations sur chaque association. Ces méthodes peuvent être consommées par les composants WebPart SharePoint, des listes ou des applications personnalisées pour afficher les relations entre les données dans une interface utilisateur (IU).  
  
## <a name="create-an-association"></a>Créer une association
 Créez une association en choisissant le **Association** contrôle dans Visual Studio **boîte à outils**, en choisissant la première entité (appelée l’entité source), puis en choisissant la deuxième entité (appelée la entité de destination). Vous pouvez définir les détails de l’association dans le **Éditeur d’associations**. Pour plus d'informations, voir [Procédure : Créer une association entre entités](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Méthodes d’association
 Applications telles que les composants WebPart SharePoint business données consomment des associations en appelant des méthodes dans la classe de service d’une entité. Vous pouvez ajouter des méthodes à la classe de service d’une entité en les sélectionnant dans le **Éditeur d’associations**.  
  
 Par défaut, le **Éditeur d’associations** ajoute une méthode de Navigation de l’Association aux entités source et de destination. Dans l’entité source, une méthode de Navigation de l’Association permet aux consommateurs de récupérer une liste d’entités de destination. Dans l’entité de destination, une méthode de Navigation de l’Association permet aux consommateurs de récupérer l’entité source qui est lié à une entité de destination.  
  
 Vous devez ajouter le code pour chacune de ces méthodes pour retourner les informations appropriées. Vous pouvez également ajouter d’autres types de méthodes pour prendre en charge des scénarios plus avancés. Pour plus d’informations sur chacune de ces méthodes, consultez [pris en charge les opérations](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Types d’associations
 Vous pouvez créer deux types d’associations dans le concepteur BDC : des associations clé étrangère et des associations sans clé étrangère.  
  
### <a name="foreign-key-based-association"></a>Association de clé étrangère
 Vous pouvez créer une association de clé étrangère en liant un identificateur dans l’entité source pour les descripteurs de type définis dans l’entité de destination. Cette relation permet aux consommateurs du modèle fournir une interface utilisateur améliorée pour les utilisateurs. Par exemple, un formulaire dans Outlook qui permet à un utilisateur de créer une commande client qui peut afficher les clients dans une liste déroulante ; ou une liste de commandes client dans SharePoint qui permet aux utilisateurs d’ouvrir une page de profil pour un client.  
  
 Pour créer une association de clé étrangère, concernent les identificateurs et descripteurs de type qui partagent les mêmes nom et type. Par exemple, vous pouvez créer une association de clé étrangère entre une `Contact` entité et un `SalesOrder` entité. Le `SalesOrder` renvoyait un `ContactID` descripteur de type dans le cadre du paramètre de retour des méthodes de recherche ou de recherche spécifique. Les deux descripteurs de type s’affichent dans le **Éditeur d’associations**. Pour créer une relation de clé étrangère entre la `Contact` entité et `SalesOrder` entité, choisissez le `ContactID` identificateur en regard de chacun de ces champs.  
  
 Ajoutez le code à la méthode de navigateur d’associations de l’entité source qui retourne une collection d’entités de destination. L’exemple suivant retourne les commandes pour un contact.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Ajoutez le code à la méthode du navigateur de l’Association de l’entité de destination qui retourne une entité source. L’exemple suivant retourne le contact est lié à la commande client.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Association sans clé étrangère
 Vous pouvez créer une association sans mappage des identificateurs pour les descripteurs de type de champ. Créez ce type d’association lorsque l’entité source ne dispose pas d’une relation directe avec l’entité de destination. Par exemple, un `SalesOrderDetail` table n’a pas d’une clé étrangère qui mappe à une clé primaire dans une `Contact` table.  
  
 Si vous souhaitez afficher des informations dans le `SalesOrderDetail` table qui est lié à un `Contact`, vous pouvez créer une association sans clé étrangère entre la `Contact` entité et `SalesOrderDetail` entité.  
  
 Dans la méthode de Navigation de l’Association de la `Contact` entité, retournée le `SalesOrderDetail` entités en joignant les tables, ou en appelant une procédure stockée.  
  
 L’exemple suivant renvoie des informations sur toutes les commandes client en joignant les tables.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 Dans la méthode de Navigation de l’Association de la `SalesOrderDetail` entité, retourner connexe `Contact`. Cela est illustré par l'exemple suivant.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Voir aussi
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Guide pratique pour Créer une association entre entités](../sharepoint/how-to-create-an-association-between-entities.md)  
