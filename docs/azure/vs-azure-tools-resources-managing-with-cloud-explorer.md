---
title: Gestion des ressources Azure avec Cloud Explorer | Microsoft Docs
description: Découvrez comment utiliser Cloud Explorer pour rechercher et gérer des ressources Azure dans Visual Studio.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 919eb350f655dda2b96527b1e37f0ec027dd922d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937407"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Gérer les ressources associées à vos comptes Azure dans Visual Studio Cloud Explorer

Cloud Explorer vous permet de visualiser vos groupes de ressources et vos ressources Azure, d’inspecter leurs propriétés et d’exécuter des actions de diagnostic de développeur essentielles à partir de Visual Studio.

Tout comme le [Portail Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer repose sur la pile Azure Resource Manager. Par conséquent, Cloud Explorer comprend des ressources, telles que les groupes de ressources Azure, et des services Azure, notamment Logic Apps et API Apps, et prend en charge le [contrôle d’accès en fonction du rôle](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017](https://www.visualstudio.com/downloads/) avec la **charge de travail Azure** sélectionnée, ou une version antérieure de Visual Studio avec le [Kit de développement logiciel (SDK) Microsoft Azure pour .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Compte Microsoft Azure : si vous ne possédez pas de compte, vous pouvez [vous inscrire à un essai gratuit](http://go.microsoft.com/fwlink/?LinkId=623901) ou [activer les avantages de votre abonnement Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Pour afficher Cloud Explorer, sélectionnez **Afficher** > **Cloud Explorer** sur la barre de menus.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Ajouter un compte Azure à Cloud Explorer

Pour afficher les ressources associées à un compte Azure, vous devez commencer par ajouter le compte à Cloud Explorer.

1. Dans **Cloud Explorer**, sélectionnez **Paramètres de compte Azure**.

   ![Icône des paramètres de compte Azure Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Sélectionnez **Gérer les comptes**.

   ![Lien Ajouter un compte Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Connectez-vous au compte Azure dont vous souhaitez parcourir les ressources.

1. Une fois que vous êtes connecté à un compte Azure, les abonnements associés à ce compte s’affichent. Cochez les cases des abonnements de compte que vous souhaitez parcourir, puis sélectionnez **Appliquer**.

   ![Cloud Explorer : sélectionnez les abonnements Azure à afficher](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Une fois que vous avez sélectionné les abonnements dont vous souhaitez parcourir les ressources, les abonnements et les ressources s’affichent dans Cloud Explorer.

   ![Listing des ressources Cloud Explorer pour un compte Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Supprimer un compte Azure de Cloud Explorer

1. Dans **Cloud Explorer**, sélectionnez **Gestion des comptes**.

   ![Icône des paramètres de compte Azure Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. En regard du compte à supprimer, sélectionnez **Gestion des comptes**.

   ![Icône des paramètres de compte Azure Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Choisissez **Supprimer** pour supprimer un compte.

    ![Boîte de dialogue Gestion des comptes de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Afficher les types ou les groupes de ressources

Pour afficher vos ressources Azure, vous pouvez choisir l’affichage **Types de ressources** ou **Groupes de ressources**.

1. Dans **Cloud Explorer**, sélectionnez la liste déroulante d’affichage des ressources.

   ![Liste déroulante Cloud Explorer pour sélectionner l’affichage des ressources souhaité](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Dans le menu contextuel, sélectionnez l’affichage souhaité :

   * Affichage **Types de ressources** : l’affichage courant utilisé sur le [Portail Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) affiche vos ressources Azure classées par type, par exemple applications web, comptes de stockage et machines virtuelles.
   * Affichage **Groupes de ressources** : organise les ressources Azure en fonction du groupe de ressources Azure auquel elles sont associées. Un groupe de ressources est un regroupement de ressources Azure, généralement utilisé par une application spécifique. Pour en savoir plus sur les groupes de ressources Azure, consultez [Présentation d’Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   L’image suivante compare les deux affichages de ressources :

   ![Comparaison des affichages des ressources Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Afficher et parcourir les ressources dans Cloud Explorer

Pour accéder à une ressource Azure et afficher ses informations dans Cloud Explorer, développez le type de l’élément ou le groupe de ressources associé, puis sélectionnez la ressource. Lorsque vous sélectionnez une ressource, les informations apparaissent dans les deux onglets, **Actions** et **Propriétés**, en bas de Cloud Explorer.

* Onglet **Actions** : liste les actions possibles dans Cloud Explorer pour la ressource sélectionnée. Vous pouvez également voir ces options en cliquant avec le bouton droit sur la ressource pour afficher son menu contextuel.

* Onglet **Propriétés** : affiche les propriétés de la ressource, notamment son type, ses paramètres régionaux et le groupe de ressources auquel elle est associée.

L’image suivante montre un exemple de comparaison de ce qui apparaît sur chaque onglet pour un service App Service :

  ![Capture d’écran de Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Chaque ressource dispose de l'action **Ouvrir dans le portail**. Lorsque vous sélectionnez cette action, Cloud Explorer affiche la ressource sélectionnée dans le [portail Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). La fonctionnalité **Ouvrir dans le portail** est particulièrement pratique pour parcourir des ressources profondément imbriquées.

Des actions et des valeurs de propriétés supplémentaires peuvent également s’afficher en fonction de la ressource Azure. Par exemple, les applications web et les applications logiques ont également les actions **Ouvrir dans un navigateur** et **Attacher le débogueur** en plus de l’action **Ouvrir dans le portail**. Les actions d’ouverture des éditeurs apparaissent lorsque vous sélectionnez un objet Blob, File d'attente ou Table de compte de stockage. Les applications Azure ont des propriétés **URL** et **État**, tandis que les ressources de stockage ont des propriétés clé et chaîne de connexion.

## <a name="find-resources-in-cloud-explorer"></a>Trouver des ressources dans Cloud Explorer

Pour trouver des ressources portant un nom spécifique dans les abonnements de votre compte Azure, entrez le nom dans la zone **Recherche** de Cloud Explorer.

  ![Trouver des ressources dans Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Lorsque vous entrez des caractères dans la zone **Recherche**, seules les ressources qui correspondent à ces caractères apparaissent dans l’arborescence de ressources.
