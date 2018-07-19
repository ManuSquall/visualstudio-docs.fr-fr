---
title: 'Comment : ajouter une méthode de mise à jour | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3004e6b83f98ccf82e6086c4669618ef4fb48c8c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755741"
---
# <a name="how-to-add-an-updater-method"></a>Comment : ajouter une méthode de mise à jour
  Vous pouvez autoriser les utilisateurs à mettre à jour des données métiers dans une liste externe SharePoint en créant un *mise à jour du* (méthode). Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Pour créer une méthode de mise à jour  
  
1.  Dans le concepteur BDC, choisissez une entité.  
  
2.  Dans la barre de menus, choisissez **vue** > **Windows autres** > **détails de méthode BDC**.  
  
     La fenêtre Détails de méthode BDC s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de mise à jour du**.  
  
     Visual Studio ajoute les éléments suivants au modèle. Ces éléments apparaissent dans la fenêtre Détails de méthode BDC.  
  
    -   Une méthode nommée **mise à jour**.  
  
    -   Un paramètre d’entrée pour la méthode.  
  
    -   Un descripteur de type pour le paramètre. Par défaut, Visual Studio utilise le descripteur de type d’entité que vous avez définie pour la méthode de recherche (par exemple : Contact).  
  
    -   Une instance de méthode pour la méthode.  
  
     Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Si l’identificateur du type d’entité représente un champ dans une table de base de données qui n’est pas automatiquement généré, définissez le **champ de pré-mise** propriété **True**.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service du fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**.  
  
     Le fichier de code de service entité s’ouvre dans le **éditeur de Code**. Pour plus d’informations sur ce fichier, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez le code à la méthode de mise à jour pour mettre à jour des données. L’exemple suivant met à jour les informations d’un contact dans la base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Voir aussi
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
 
