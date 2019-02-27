---
title: Configuration des administrateurs pour les abonnements cloud | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/28/2018
ms.topic: conceptual
description: Configuration des administrateurs pour les abonnements cloud
searchscope: VS Subscription
ms.openlocfilehash: fafac6b36c2abd34f47d4321155d123ce7cecd90
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841443"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Configurer des administrateurs pour les abonnements cloud Visual Studio

Les abonnements cloud Visual Studio sont gérés par des administrateurs. Ces personnes peuvent attribuer des abonnements, modifier des assignations, ajouter ou supprimer des abonnements et effectuer d’autres tâches de gestion des abonnements.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Le propriétaire de l’abonnement Azure est le premier administrateur

Quand vous achetez des abonnements cloud Visual Studio, en tant que propriétaire de l’abonnement Azure utilisé pour effectuer les achats, vous êtes automatiquement configuré comme administrateur de ces abonnements.

Vous pouvez acheter des abonnements cloud via [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) ou en contactant un fournisseur de solutions cloud. Si vous effectuez l’achat via Visual Studio Marketplace, vous aurez la possibilité de gérer les utilisateurs à la fin de celui-ci. Le choix de cette option vous dirige vers le portail de gestion des abonnements Visual Studio - [ https://manage.visualstudio.com ](https://manage.visualstudio.com).

Une fois que vous avez acheté des abonnements, vous pouvez visiter le [portail de gestion](https://manage.visualstudio.com) à tout moment. Il vous suffit de vous connecter au portail et de sélectionner l’abonnement Azure approprié dans l’angle supérieur gauche.

En tant que propriétaire de l’abonnement Azure utilisé pour acheter les abonnements cloud, vous pouvez également affecter des administrateurs supplémentaires.

## <a name="add-administrators"></a>Ajouter des administrateurs

Pour ajouter des administrateurs :

1. Connectez-vous au portail Azure sur [portal.azure.com](https://portal.azure.com).
2. Connectez-vous avec le compte que vous avez utilisé pour acheter les abonnements cloud Visual Studio.
3. Dans le volet de navigation gauche, faites défiler vers le bas jusqu’à **Gestion des coûts + facturation**.
4. Dans la liste **Mes abonnements**, sélectionnez l’abonnement Azure que vous avez utilisé pour effectuer l’achat.
5. Cliquez sur **Contrôle d’accès**, qui se trouve près du haut de la liste dans le volet de navigation gauche.
6. Cliquez sur l’onglet **Ajouter** en haut de la page.
7. Dans le volet volant à droite, cliquez sur le nom de l’abonné qui doit devenir administrateur.
8. Cliquez sur la liste déroulante **Rôle** en haut du volet, faites défiler vers le bas et sélectionnez **Administrateur de l’accès utilisateur**.
9. Cliquez sur **Enregistrer**.

L’abonné que vous avez désigné apparaît au centre de la page et son rôle est « Administrateur de l’accès utilisateur ».

Le nouvel administrateur peut maintenant se connecter au [portail de gestion](https://manage.visualstudio.com), sélectionner le même abonnement Azure qui a été utilisé pour acheter les abonnements cloud à partir de la liste dans l’angle supérieur gauche de la page et commencer à gérer ces abonnements.


> [!NOTE]
> Si vous voyez que des utilisateurs bénéficiant d’un accès leur permettant de modifier vos abonnements cloud alors que vous ne les avez pas établis en tant qu’administrateurs, c’est peut-être qu’ils ont des rôles qui leur permettent de gérer des abonnements dans l’abonnement Azure sous-jacent. Ceci inclut les rôles suivants : propriétaire, contributeur, administrateur de service ou coadministrateur. Pour plus d’informations, consultez [Ajouter des gestionnaires de facturation](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Pour plus d’informations sur les abonnements cloud Visual Studio, consultez la [vue d’ensemble](vscloud-overview.md) sous Achat d’abonnements cloud. Pour acheter des abonnements cloud Visual Studio, accédez à Visual Studio Marketplace à l’adresse [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).