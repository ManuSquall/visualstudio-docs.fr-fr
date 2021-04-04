---
title: 'Comment : ajouter une méthode de recherche spécifique | Microsoft Docs'
description: Pour obtenir une instance d’entité, ajoutez une méthode de recherche. Le service BDC appelle la méthode lorsqu’un utilisateur choisit une entité dans un composant WebPart de données métier ou une liste externe.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87f5b0cf86178b88b1611f4b0ce8a4bbacde780e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216798"
---
# <a name="how-to-add-a-specific-finder-method"></a>Comment : ajouter une méthode de recherche spécifique
  Vous pouvez retourner une instance d’entité unique en créant une méthode de *recherche spécifique* . Le service de connectivité de données métiers (BDC) exécute la méthode de recherche spécifique lorsqu’un utilisateur choisit une entité dans un composant WebPart de données métier ou une liste externe. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Pour créer une méthode de recherche spécifique

1. Dans le **concepteur BDC**, choisissez une entité.

    Pour plus d’informations sur l’ajout d’une entité au **concepteur BDC** dans Visual Studio, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Dans la barre de menus, choisissez **Afficher**  >  **les autres fenêtres**, détails de la **méthode BDC**.

    La fenêtre Détails de la **méthode BDC** s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Dans la liste **Ajouter une méthode** , choisissez **créer une méthode de recherche spécifique**.

    Visual Studio ajoute les éléments suivants au modèle. Ces éléments s’affichent dans la fenêtre Détails de la **méthode BDC** .

   - Une méthode.

   - Paramètre d’entrée pour la méthode.

   - Paramètre de retour de la méthode.

   - Descripteur de type pour chaque paramètre.

   - Instance de méthode pour la méthode.

     Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Ouvrez la fenêtre **Propriétés** de Visual Studio.

5. Configurez le descripteur de type du paramètre de retour en tant que descripteur de type d’entité. Pour plus d’informations sur la création d’un descripteur de type d’entité, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Vous n’avez pas besoin d’effectuer cette étape si vous avez ajouté une méthode de recherche à l’entité. Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche.

   > [!NOTE]
   > Si le champ d’identificateur du type d’entité représente un champ dans une table de base de données qui est générée automatiquement, affectez la valeur **true** à la propriété **en lecture seule** du champ d’identificateur.

6. Dans la fenêtre **Détails de méthode** , choisissez l’instance de méthode de la méthode.

7. Dans la **fenêtre Propriétés**, définissez la propriété **Return Parameter Name** sur le nom du paramètre de retour de la méthode. Pour plus d’informations sur les propriétés d’instance de méthode, consultez [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier de code de service qui a été généré pour l’entité, puis choisissez **afficher le code**.

    Le fichier de code du service d’entité s’ouvre dans l’éditeur de code. Pour plus d’informations sur le fichier de code du service d’entité, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Ajoutez du code à la méthode de recherche spécifique. Ce code effectue les tâches suivantes :

   - Récupère un enregistrement à partir d’une source de données.

   - Retourne une entité au service BDC.

     L’exemple suivant retourne un contact à partir de l’exemple de base de données AdventureWorks pour SQL Server.

     > [!NOTE]
     > Remplacez la valeur du `ServerName` champ par le nom de votre serveur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>Voir aussi
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
