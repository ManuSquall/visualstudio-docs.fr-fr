---
title: Gérer les licences surutilisées | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent résoudre les problèmes de surutilisation d’abonnements
ms.openlocfilehash: 23a0888a670c10af4447d7a097067ffe4fe70c0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783449"
---
# <a name="overallocated-subscriptions"></a>Abonnements surutilisés

Les commandes sont parfois modifiées après l’ajout des abonnés. Le risque est que le nombre d’abonnements attribués dépasse le nombre de licences détenues par votre entreprise. Quand cela se produit, l’onglet Abonnés affiche une alerte, accompagnée d’informations détaillées.

> [!NOTE]
> Les scénarios de surutilisation ne sont pas autorisés dans les programmes Open License.  En outre, d’autres programmes peuvent afficher ces informations différemment dans le portail.
>
> [!div class="mx-imgBorder"]
> ![Notification de surutilisation d’abonnements](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>Résolution des abonnements surutilisés

Pour résoudre des licences surutilisées :

1. Cliquez sur le texte d’alerte. Vous voyez s’afficher une liste filtrée des abonnés pour lesquels le niveau et la date d’expiration de l’abonnement attribué donne lieu à une surutilisation de licences. 

2. Supprimez des abonnés de façon à résoudre le problème de surutilisation des licences. 

3. La vue d’ensemble sur le côté gauche de la page est ensuite actualisée pour montrer qu’il n’y a plus de problème et retirer toutes les notifications de surutilisation. 

## <a name="billing-and-true-up"></a>Facturation et régularisation

Si votre organisation a un Contrat Entreprise (EA), les administrateurs peuvent attribuer des abonnements sans les acheter, en les payant plus tard par le biais d’un processus de rapprochement appelé « régularisation ».  En cas de surutilisation, le nombre maximal d’abonnements attribués aux utilisateurs durant la « régularisation » est facturé à votre entreprise.  Cela est vrai même si le nombre actuel d’abonnements ne correspond plus au nombre maximal d’abonnements attribués au moment de la régularisation.  Pour en savoir plus sur le contrôle de l’utilisation maximum, consultez la rubrique [Utilisation maximum](maximum-usage.md).

> [!Important]
> Si des abonnements Visual Studio avec GitHub Enterprise sont attribués par des administrateurs d’abonnement Visual Studio alors qu’ils n’ont jamais été achetés, les administrateurs GitHub Enterprise au sein de l’organisation ne les voient pas. Pour vérifier que les abonnements GitHub Enterprise sont visibles, un achat comprenant **au moins** un abonnement Visual Studio Professional avec GitHub Enterprise ou Visual Studio Enterprise avec GitHub Enterprise doit être effectué à la première attribution des abonnements.  
>
> Il appartient au client de vérifier qu’à chaque abonnement GitHub attribué correspond un abonnement Visual Studio avec GitHub attribué dans le portail Gérer afin de respecter les conditions de licence pour cet abonnement.

Découvrez-en plus sur la gestion des [abonnements Visual Studio avec GitHub Enterprise](assign-github.md).

## <a name="support-resources"></a>Ressources de support

- Pour obtenir de l’aide concernant les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, contactez le [support des abonnements](https://visualstudio.microsoft.com/subscriptions/support/) Visual Studio.
