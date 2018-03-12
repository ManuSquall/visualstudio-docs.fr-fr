---
title: "Comment : ajouter une méthode de recherche | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c2c7bf2eed200b8ed223f266ca35b5af90862cd6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-finder-method"></a>Comment : ajouter une méthode de recherche
  Pour activer le service de connectivité de données métiers afficher la liste des entités dans une liste ou un composant WebPart, vous devez créer un *recherche* (méthode). Une méthode de recherche est une méthode spéciale qui retourne une collection d’instances d’entité. Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Pour créer une méthode de recherche  
  
1.  Dans le concepteur BDC, choisissez une entité.  
  
     Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **détails de méthode BDC**.  
  
     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations sur la **détails de méthode BDC** fenêtre, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de recherche**.  
  
     Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.  
  
4.  Configurez le descripteur de type en tant que descripteur de type entité collection. Pour plus d’informations sur la création d’un descripteur de type de collection entité, consultez [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Vous n’avez pas à effectuer cette étape si vous avez ajouté une méthode de recherche spécifique à l’entité. Visual Studio utilise le descripteur de type que vous avez définie dans la méthode de recherche spécifique.  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**. Pour plus d’informations sur le fichier de code de service, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Ajoutez le code à la méthode de recherche. Ce code exécute les tâches suivantes :  
  
    -   Récupère les données à partir d’une source de données.  
  
    -   Retourne une liste d’entités au service BDC.  
  
     L’exemple suivant retourne une collection de `Contact` entités à l’aide des données à partir de la base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  