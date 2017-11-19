---
title: "Comment : ajouter une méthode de création | Documents Microsoft"
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 354d3f574515fcc9e8417e817363f9bbe7327f06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-creator-method"></a>Comment : ajouter une méthode de création
  Une méthode de création ajoute de nouvelles données à la source de données d’une entité. Le service de connectivité de données métiers (BDC) appelle cette méthode lorsque les utilisateurs choisissent le **un nouvel élément** bouton sur le ruban d’une liste qui est basée sur le modèle. Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Pour ajouter une méthode de création  
  
1.  Dans le concepteur BDC, choisissez une entité.  
  
2.  Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **détails de méthode BDC**.  
  
     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de créateur**.  
  
     Visual Studio ajoute les éléments suivants au modèle, et ces éléments apparaissent dans le **détails de méthode BDC** fenêtre.  
  
    -   Une méthode nommée **créer**.  
  
    -   Un paramètre d’entrée pour la méthode.  
  
    -   Un paramètre de retour de la méthode.  
  
    -   Descripteurs pour les paramètres de type.  
  
    -   Une instance de méthode pour la méthode.  
  
     Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**.  
  
     Le fichier de code de service entité s’ouvre dans l’éditeur de Code. Pour plus d’informations sur le fichier de code de service entité, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez le code à la méthode de création qui ajoute des données à la source de données. L’exemple suivant ajoute un contact à la base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  