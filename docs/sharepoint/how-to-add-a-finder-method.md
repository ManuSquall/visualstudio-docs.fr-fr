---
title: 'Procédure : Ajouter une méthode de recherche | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40a3cb4457f3078e843b89349fd850d83b8a1c67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963451"
---
# <a name="how-to-add-a-finder-method"></a>Procédure : Ajouter une méthode de recherche
  Pour activer le service de connectivité de données métiers (BDC) afficher une liste d’entités dans une liste ou un composant WebPart, vous devez créer un *Finder* (méthode). Une méthode de recherche est une méthode spéciale qui retourne une collection d’instances d’entité. Pour plus d’informations, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Pour créer une méthode de recherche  
  
1. Sur le **concepteur BDC**, choisir une entité.  
  
    Pour plus d'informations, voir [Procédure : Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2. Dans la barre de menus, choisissez **vue** > **Windows autres** > **détails de méthode BDC**.  
  
    Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations sur la **détails de méthode BDC** fenêtre, consultez [vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Dans le **ajouter une méthode** , choisissez **créer une méthode de recherche**.  
  
    Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.  
  
4. Configurez le descripteur de type en tant qu’un descripteur de type de collection entité. Pour plus d’informations sur la création d’un descripteur de type de collection entité, consultez [Comment : Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
   > [!NOTE]  
   >  Il est inutile d’effectuer cette étape si vous avez ajouté une méthode de recherche spécifique à l’entité. Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche spécifique.  
  
5. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service du fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**. Pour plus d’informations sur le fichier de code de service, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6. Ajoutez le code à la méthode de recherche. Ce code exécute les tâches suivantes :  
  
   - Récupère les données à partir d’une source de données.  
  
   - Retourne une liste d’entités au service BDC.  
  
     L’exemple suivant retourne une collection de `Contact` entités à l’aide des données à partir de la base de données AdventureWorks pour SQL Server.  
  
   > [!NOTE]  
   >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
