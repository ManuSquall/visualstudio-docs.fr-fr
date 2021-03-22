---
title: Configuration des administrateurs pour les abonnements Visual Studio mensuels | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/21/2021
ms.topic: how-to
description: Configuration des administrateurs pour les abonnements mensuels
ms.openlocfilehash: 220f5986bb06b638504379b63e911f9bb62926b5
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776946"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Configurer des administrateurs pour les abonnements mensuels Visual Studio

Les abonnements mensuels Visual Studio sont gérés par les administrateurs. Ces personnes peuvent attribuer des abonnements, modifier des assignations, ajouter ou supprimer des abonnements et effectuer d’autres tâches de gestion des abonnements.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Le propriétaire de l’abonnement Azure est le premier administrateur

Lorsque vous achetez des abonnements mensuels Visual Studio, en tant que propriétaire de l’abonnement Azure utilisé pour effectuer les achats, vous êtes automatiquement configuré en tant qu’administrateur de ces abonnements.

Vous pouvez acheter des abonnements mensuels par le biais du [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)ou en contactant un fournisseur de solutions Cloud. Si vous effectuez l’achat via Visual Studio Marketplace, vous aurez la possibilité de gérer les utilisateurs à la fin de celui-ci. Le choix de cette option vous permet d’atteindre le portail d’administration des abonnements Visual Studio- [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Une fois que vous avez acheté des abonnements, vous pouvez accéder au [portail d’administration](https://manage.visualstudio.com) à tout moment. Connectez-vous simplement au portail et sélectionnez l’abonnement Azure approprié dans l’angle supérieur gauche.

En tant que propriétaire de l’abonnement Azure utilisé pour acheter les abonnements mensuels, vous pouvez également affecter des administrateurs supplémentaires.

## <a name="add-admins"></a>Add admins

Pour ajouter des administrateurs :

1. Connectez-vous à la Portail Azure sur [Portal.Azure.com](https://portal.azure.com).
2. Connectez-vous avec le compte que vous avez utilisé pour acheter les abonnements mensuels Visual Studio.
3. Sous **services Azure**, choisissez **Cost Management + facturation**.
   > [!div class="mx-imgBorder"]
   > ![Choisir Cost Management + facturation sous services Azure](_img/cloud-admin/azure-cost-billing.png "Choisir Cost Management dans le groupe services Azure")
4. Dans la liste **mes abonnements** , choisissez l’abonnement Azure que vous avez utilisé pour effectuer l’achat.
   > [!div class="mx-imgBorder"]
   > ![Choisir un abonnement](_img/cloud-admin/subscription-list.png "Choisissez l’abonnement Azure que vous souhaitez utiliser pour effectuer votre achat.")
5. Cliquez sur **contrôle d’accès (IAM)**, situé près du haut de la liste dans le volet de navigation gauche.
6. Cliquez sur l’onglet **Ajouter** en haut de la page.
7. Cliquez sur **Ajouter une attribution de rôle**.
   > [!div class="mx-imgBorder"]
   > ![Choisissez contrôle d’accès, ajouter, ajouter une attribution de rôle](_img/cloud-admin/access-control-add.png "Choisissez contrôle d’accès dans la liste de gauche, puis choisissez Ajouter.")
8. Dans le volet de menu volant situé à droite, cliquez sur la liste déroulante **Rôle** en haut du volet, faites défiler vers le bas, puis sélectionnez **Administrateur de l’accès utilisateur**.
9. Faites défiler la liste des utilisateurs jusqu’à l’utilisateur auquel vous souhaitez attribuer un rôle d’administrateur, puis sélectionnez-le. 
   > [!div class="mx-imgBorder"]
   > ![Choisir un rôle, administrateur de l’accès utilisateur](_img/cloud-admin/add-role-user-access-admin.png "Choisissez rôle, sélectionnez administrateur de l’accès utilisateur, puis sélectionnez le nom de l’utilisateur pour en faire un administrateur.")
10. Cliquez sur **Enregistrer**.
11. Cliquez sur l’onglet **Attributions de rôles** pour vérifier que l’utilisateur sélectionné apparaît désormais en tant qu’administrateur de l’accès utilisateur.

Le nouvel administrateur peut maintenant se connecter au [portail d’administration](https://manage.visualstudio.com), sélectionner le même abonnement Azure que celui qui a été utilisé pour acheter les abonnements mensuels dans la liste située dans le coin supérieur gauche de la page et commencer à gérer ces abonnements.

> [!NOTE]
> Si vous constatez que les utilisateurs ont accès à la modification de vos abonnements mensuels que vous n’avez pas établis en tant qu’administrateurs, ils peuvent avoir des rôles dans l’abonnement Azure sous-jacent qui leur permet de gérer les abonnements. Ces rôles sont les suivants : propriétaire, collaborateur, administrateur de service ou coadministrateur. Pour plus d’informations, consultez [Ajouter des gestionnaires de facturation](/azure/devops/organizations/billing/add-backup-billing-managers).

Pour plus d’informations sur les abonnements mensuels Visual Studio, consultez la [vue d’ensemble](vscloud-overview.md) sous achat d’abonnements. Pour acheter des abonnements mensuels Visual Studio, visitez le Visual Studio Marketplace à l’adresse [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)