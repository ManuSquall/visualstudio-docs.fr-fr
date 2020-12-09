---
title: 'Comment : ajouter une méthode de recherche | Microsoft Docs'
description: Ajoutez une méthode de recherche dans Visual Studio, qui permet au service BDC (Business Data Connectivity) d’afficher une liste d’entités dans une liste ou un composant WebPart SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7e2bb74278194878ed4496c12c918707cdc1e6e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915087"
---
# <a name="how-to-add-a-finder-method"></a>Comment : ajouter une méthode de recherche
  Pour permettre au service BDC (Business Data Connectivity) d’afficher une liste d’entités dans un composant WebPart ou une liste, vous devez créer une méthode de *recherche* . Une méthode de recherche est une méthode spéciale qui retourne une collection d’instances d’entité. Pour plus d’informations, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Pour créer une méthode de recherche

1. Dans le **concepteur BDC**, choisissez une entité.

    Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Dans la barre de menus, choisissez **Afficher**  >  **les autres** détails de la  >  **méthode BDC** Windows.

    La fenêtre Détails de la **méthode BDC** s’ouvre. Pour plus d’informations sur la fenêtre Détails de la **méthode BDC** , consultez [vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Dans la liste **Ajouter une méthode** , choisissez **créer une méthode de recherche**.

    Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.

4. Configurez le descripteur de type comme un descripteur de type de collection d’entités. Pour plus d’informations sur la création d’un descripteur de type de collection d’entités, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Vous n’avez pas à effectuer cette étape si vous avez ajouté une méthode de recherche spécifique à l’entité. Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche spécifique.

5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier de code de service qui a été généré pour l’entité, puis choisissez **afficher le code**. Pour plus d’informations sur le fichier de code de service, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Ajoutez du code à la méthode Finder. Ce code effectue les tâches suivantes :

   - Récupère des données d’une source de données.

   - Retourne une liste d’entités au service BDC.

     L’exemple suivant retourne une collection d' `Contact` entités à l’aide des données de l’exemple de base de données AdventureWorks pour SQL Server.

   > [!NOTE]
   > Remplacez la valeur du `ServerName` champ par le nom de votre serveur.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
