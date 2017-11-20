---
title: "Comment : ajouter une méthode de mise à jour | Documents Microsoft"
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3270e35f270ba40534d3a3a9fce679bfd8f6534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-updater-method"></a>Comment : ajouter une méthode de mise à jour
  Vous pouvez activer les utilisateurs mettre à jour des données métiers dans une liste externe SharePoint en créant une *Updater* (méthode). Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Pour créer une méthode de mise à jour  
  
1.  Dans le concepteur BDC, choisissez une entité.  
  
2.  Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **détails de méthode BDC**.  
  
     La fenêtre Détails de méthode BDC s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de mise à jour**.  
  
     Visual Studio ajoute les éléments suivants au modèle. Ces éléments apparaissent dans la fenêtre Détails de méthode BDC.  
  
    -   Une méthode nommée **mise à jour**.  
  
    -   Un paramètre d’entrée pour la méthode.  
  
    -   Un descripteur de type pour le paramètre. Par défaut, Visual Studio utilise le descripteur de type d’entité que vous avez définie pour la méthode de recherche (par exemple : Contact).  
  
    -   Une instance de méthode pour la méthode.  
  
     Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Si l’identificateur du type d’entité représente un champ dans une table de base de données qui n’est pas automatiquement générée, définissez le **champ de pré-mise** propriété **True**.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**.  
  
     Le fichier de code de service entité s’ouvre dans l’éditeur de Code. Pour plus d’informations sur ce fichier, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez le code à la méthode de mise à jour pour mettre à jour des données. L’exemple suivant met à jour les informations d’un contact dans la base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  