---
title: 'Comment : ajouter une méthode de recherche spécifique | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7319842d0c90b18b170fcd5e199dc255f45a3374
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758434"
---
# <a name="how-to-add-a-specific-finder-method"></a>Comment : ajouter une méthode de recherche spécifique
  Vous pouvez retourner une seule instance d’entité en créant un *recherche spécifique* (méthode). Le service de connectivité de données métiers (BDC) exécute la méthode de recherche spécifique lorsqu’un utilisateur choisit une entité dans un composant WebPart données métier ou d’une liste externe. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Pour créer une méthode de recherche spécifique
  
1.  Sur le **concepteur BDC**, choisir une entité.  
  
     Pour plus d’informations sur l’ajout d’une entité à la **concepteur BDC** dans Visual Studio, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Dans la barre de menus, choisissez **vue** > **Windows autres**, **détails de méthode BDC**.  
  
     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de recherche spécifique**.  
  
     Visual Studio ajoute les éléments suivants au modèle. Ces éléments apparaissent dans le **détails de méthode BDC** fenêtre.  
  
    -   Une méthode.  
  
    -   Un paramètre d’entrée pour la méthode.  
  
    -   Un paramètre de retour pour la méthode.  
  
    -   Un descripteur de type pour chaque paramètre.  
  
    -   Une instance de méthode pour la méthode.  
  
     Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Ouvrez Visual Studio **propriétés** fenêtre.  
  
5.  Configurez le descripteur de type du paramètre de retour comme un descripteur de type d’entité. Pour plus d’informations sur la création d’un descripteur de type d’entité, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Vous n’êtes pas obligé d’effectuer cette étape si vous avez ajouté une méthode de recherche à l’entité. Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche.  
  
    > [!NOTE]  
    >  Si le champ d’identificateur du type d’entité représente un champ dans une table de base de données qui est généré automatiquement, définissez la **en lecture seule** propriété du champ d’identificateur à **True**.  
  
6.  Dans le **détails de la méthode** fenêtre, choisissez l’instance de méthode de la méthode.  
  
7.  Dans le **fenêtre Propriétés**, définissez le **retourner un nom de paramètre** propriété le nom du paramètre de retour de la méthode. Pour plus d’informations sur les propriétés d’instance de méthode, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service du fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**.  
  
     Le fichier de code de service entité s’ouvre dans l’éditeur de Code. Pour plus d’informations sur le fichier de code de service entité, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Ajoutez le code à la méthode de recherche spécifique. Ce code exécute les tâches suivantes :  
  
    -   Récupère un enregistrement à partir d’une source de données.  
  
    -   Retourne une entité au service BDC.  
  
     L’exemple suivant retourne un contact à partir de la base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Voir aussi
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
