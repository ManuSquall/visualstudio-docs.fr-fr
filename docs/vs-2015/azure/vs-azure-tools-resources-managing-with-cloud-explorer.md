---
title: Gestion des ressources Azure avec Cloud Explorer | Microsoft Docs
description: Découvrez comment utiliser Cloud Explorer pour parcourir et de gérer des ressources Azure dans Visual Studio.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001713"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Gérer les ressources associées à vos comptes Azure dans Visual Studio Cloud Explorer

Cloud Explorer vous permet de visualiser vos ressources Azure et les groupes de ressources, inspecter leurs propriétés, et effectuer des actions de diagnostic de développeur essentielles à partir de Visual Studio. 

Comme le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer repose sur la pile Azure Resource Manager. Par conséquent, Cloud Explorer comprend des ressources telles que les groupes de ressources Azure et services Azure tels que Logic apps et API apps, et il prend en charge [contrôle d’accès en fonction du rôle](/azure/role-based-access-control/role-assignments-portal.md) (RBAC). 

## <a name="prerequisites"></a>Prérequis

* Visual Studio 2015 avec le [Microsoft Azure SDK pour .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Compte Microsoft Azure : Si vous n’avez pas un compte, vous pouvez [s’inscrire pour un essai gratuit](http://go.microsoft.com/fwlink/?LinkId=623901) ou [activer vos avantages d’abonné Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Pour afficher Cloud Explorer, sélectionnez **vue** > **Cloud Explorer** sur la barre de menus.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Ajoutez un référentiel Azure compte à Cloud Explorer

Pour afficher les ressources associées à un compte Azure, vous devez d’abord ajouter le compte à Cloud Explorer. 

1. Dans **Cloud Explorer**, sélectionnez **paramètres de compte Azure**.

   ![Icône des paramètres de compte cloud Azure dans l’Explorateur](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Sélectionnez **gérer les comptes**. 

   ![Lien d’ajouter un compte Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Connectez-vous au compte Azure dont vous souhaitez parcourir les ressources. 

1. Une fois connecté à un compte Azure, les abonnements associés à ce compte s’affiche. Sélectionnez les cases à cocher pour les abonnements de compte que vous souhaitez parcourir, puis sélectionnez **appliquer**. 

   ![Cloud Explorer : sélectionnez les abonnements Azure à afficher](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Après avoir sélectionné les abonnements dont vous souhaitez parcourir les ressources, les abonnements et les ressources s’affichent dans l’Explorateur de Cloud.

   ![Ressources Cloud Explorer pour un compte Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Supprimer un compte Azure à partir de Cloud Explorer 

1. Dans **Cloud Explorer**, sélectionnez **gestion des comptes**.

   ![Icône des paramètres de compte cloud Azure dans l’Explorateur](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. En regard du compte que vous souhaitez supprimer, sélectionnez **gérer les comptes**.

   ![Icône des paramètres de compte cloud Azure dans l’Explorateur](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Choisissez **supprimer** pour supprimer un compte.

    ![Boîte de dialogue de comptes de gestion de l’Explorateur de cloud](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Afficher les types de ressources ou groupes de ressources

Pour afficher vos ressources Azure, vous pouvez choisir une **Types de ressources** ou **groupes de ressources** vue.

1. Dans **Cloud Explorer**, sélectionnez la liste déroulante Affichage de ressources.

   ![Liste de déroulante Cloud Explorer pour sélectionner l’affichage des ressources souhaité](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Dans le menu contextuel, sélectionnez l’affichage souhaité : 

   * **Types de ressources** afficher - l’affichage courant utilisé sur le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), affiche vos ressources Azure classées par type, telles que les applications web, les comptes de stockage et les machines virtuelles. 
   * **Groupes de ressources** afficher - organise les ressources Azure par le groupe de ressources Azure avec lequel elles sont associées. Un groupe de ressources est un ensemble de ressources Azure, généralement utilisée par une application spécifique. Pour en savoir plus sur les groupes de ressources Azure, consultez [présentation d’Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   L’illustration suivante montre une comparaison entre les deux affichages de ressources :

   ![Comparaison des affichages Explorateur des ressources de cloud](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Afficher et parcourir les ressources dans Cloud Explorer

Pour accéder à une ressource Azure et afficher ses informations dans Cloud Explorer, développez l’élément type ou groupe de ressources associé, puis sélectionnez la ressource. Lorsque vous sélectionnez une ressource, les informations s’affichent dans les deux onglets, **Actions** et **propriétés** , en bas de Cloud Explorer.

* **Actions** onglet - répertorie les actions possibles dans Cloud Explorer pour la ressource sélectionnée. Vous pouvez également afficher ces options en cliquant sur la ressource pour afficher son menu contextuel.

* **Propriétés** onglet : affiche les propriétés de la ressource, telles que son type, paramètres régionaux et groupe de ressources auquel il est associé.

L’illustration suivante montre un exemple de comparaison de ce que vous voyez sous chaque onglet pour un Service d’application :

  ![Capture d’écran de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Chaque ressource dispose de l’action **ouvrir dans le portail**. Lorsque vous choisissez cette action, Cloud Explorer affiche la ressource sélectionnée dans le [Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). Le **ouvrir dans le portail** fonctionnalité est pratique pour parcourir des ressources profondément imbriquées.

Actions supplémentaires et des valeurs de propriété peuvent également apparaître en fonction de la ressource Azure. Par exemple, les applications web et des applications logiques ont également les actions **ouvrir dans un navigateur** et **attacher le débogueur** outre **ouvrir dans le portail**. Les actions d’ouverture des éditeurs apparaissent lorsque vous choisissez un objet blob de compte de stockage, une file d’attente ou une table. Applications Azure ont **URL** et **état** propriétés, tandis que les ressources de stockage ont des propriétés de chaîne de connexion et la clé.

## <a name="find-resources-in-cloud-explorer"></a>Rechercher des ressources dans Cloud Explorer

Pour trouver des ressources portant un nom spécifique dans vos abonnements de compte Azure, entrez le nom dans la **recherche** zone dans Cloud Explorer.

  ![Rechercher des ressources de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Lorsque vous entrez des caractères dans le **recherche** case, seules les ressources qui correspondent à ces caractères apparaissent dans l’arborescence de ressources.
