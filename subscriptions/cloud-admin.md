---
title: Mise en place d’administrateurs pour les abonnements mensuels . Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Mise en place d’administrateurs pour les abonnements mensuels
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78289839"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Configurer des administrateurs pour les abonnements mensuels Visual Studio

Les abonnements mensuels Visual Studio sont gérés par des administrateurs. Ces personnes peuvent attribuer des abonnements, modifier des assignations, ajouter ou supprimer des abonnements et effectuer d’autres tâches de gestion des abonnements.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Le propriétaire de l’abonnement Azure est le premier administrateur

Lorsque vous achetez des abonnements mensuels Visual Studio, en tant que propriétaire de l’abonnement Azure utilisé pour effectuer les achats, vous êtes automatiquement configuré en tant qu’administrateur pour ces abonnements.

Vous pouvez acheter des abonnements mensuels via le [Visual Studio Marketplace,](https://marketplace.visualstudio.com/subscriptions)ou en contactant un fournisseur de solutions Cloud. Si vous effectuez l’achat via Visual Studio Marketplace, vous aurez la possibilité de gérer les utilisateurs à la fin de celui-ci. Choisir cette option vous mènera au portail d’administration des abonnements Visual Studio - [https://manage.visualstudio.com](https://manage.visualstudio.com).

Une fois que vous avez acheté des abonnements, vous pouvez accéder au [portail d’administration](https://manage.visualstudio.com) à tout moment. Il suffit de vous connecter au portail et de sélectionner l’abonnement Azure approprié dans le coin supérieur gauche.

En tant que propriétaire de l’abonnement Azure utilisé pour l’achat des abonnements mensuels, vous pouvez également affecter des administrateurs supplémentaires.

## <a name="add-administrators"></a>Ajouter des administrateurs

Pour ajouter des administrateurs :

1. Connectez-vous au portail Azure sur [portal.azure.com](https://portal.azure.com).
2. Connectez-vous au compte que vous avez utilisé pour acheter les abonnements mensuels Visual Studio.
3. Sous **les services Azure**, choisissez **La gestion des coûts et la facturation.**
   > [!div class="mx-imgBorder"]
   > ![Choisissez la gestion des coûts et la facturation sous les services Azure](_img/cloud-admin/azure-cost-billing.png)
4. Dans la liste **Mes abonnements**, sélectionnez l’abonnement Azure que vous avez utilisé pour effectuer l’achat.
   > [!div class="mx-imgBorder"]
   > ![Choisissez l’abonnement](_img/cloud-admin/subscription-list.png)
5. Cliquez **sur le contrôle d’accès (IAM)**, qui est situé près du haut de la liste dans le volet de navigation gauche.
6. Cliquez sur l’onglet **Ajouter** en haut de la page.
7. Cliquez **sur Ajouter l’affectation de rôle**.
   > [!div class="mx-imgBorder"]
   > ![Choisissez le contrôle d’accès, ajouter, ajouter l’affectation de rôle](_img/cloud-admin/access-control-add.png)
8. Dans le volet de menu volant situé à droite, cliquez sur la liste déroulante **Rôle** en haut du volet, faites défiler vers le bas, puis sélectionnez **Administrateur de l’accès utilisateur**.
9. Faites défiler la liste des utilisateurs jusqu’à l’utilisateur auquel vous souhaitez attribuer un rôle d’administrateur, puis sélectionnez-le. 
   > [!div class="mx-imgBorder"]
   > ![Choisissez le rôle, l’administrateur d’accès à l’utilisateur](_img/cloud-admin/add-role-user-access-admin.png)
10. Cliquez sur **Enregistrer**.
11. Cliquez sur l’onglet **Attributions de rôles** pour vérifier que l’utilisateur sélectionné apparaît désormais en tant qu’administrateur de l’accès utilisateur.

Le nouvel administrateur peut désormais se connecter au [portail d’administration,](https://manage.visualstudio.com)sélectionner le même abonnement Azure qui a été utilisé pour acheter les abonnements mensuels de la liste dans le coin supérieur gauche de la page, et commencer à gérer ces abonnements.

> [!NOTE]
> Si vous voyez des utilisateurs ayant accès à la modification de vos abonnements mensuels que vous n’avez pas établis en tant qu’administrateurs, ils peuvent avoir des rôles dans l’abonnement Azure sous-jacent qui leur permettent de gérer les abonnements. Ces rôles comprennent : propriétaire, contributeur, administrateur de service ou co-administrateur. Pour plus d’informations, visitez [Add billing managers](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Pour plus d’informations sur les abonnements mensuels Visual Studio, consultez les abonnements [Aperçu](vscloud-overview.md) sous Achat. Pour acheter des abonnements mensuels Visual [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Studio, visitez le Visual Studio Marketplace à .

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Attribuer des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)



