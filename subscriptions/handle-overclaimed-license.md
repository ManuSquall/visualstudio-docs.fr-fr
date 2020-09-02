---
title: Gérer les licences surallouées | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent résoudre les abonnements sur-alloués
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453716"
---
# <a name="over-allocated-subscriptions"></a>Abonnements alloués
Les commandes sont parfois modifiées après l’ajout des abonnés. Le risque est que le nombre d’abonnements attribués dépasse le nombre de licences détenues par votre entreprise. C’est ce que l’on appelle « sur-allocation ».  

Pour afficher vos allocations abonnement utilise, cliquez sur l’icône en haut à gauche pour ouvrir le volet allocations.  

> [!NOTE]
> Les allocations excessives ne sont pas autorisées dans les programmes de licence Open.  En outre, d’autres programmes peuvent afficher ces informations différemment dans le portail.
>
> [!div class="mx-imgBorder"]
> ![Notification de surutilisation d’abonnements](_img/over-claimed/over-claimed-alert.png "Le nombre de surallocations est indiqué dans la vue d’ensemble et est représenté par la barre hachée sur le graphique pour chaque type d’abonnement.")

Notez que l’affichage utilise une barre hachée pour indiquer des abonnements sur-alloués.  Le nombre de surallocations pour tous les types d’abonnements est inclus dans la section vue d’ensemble en haut, et chaque niveau d’abonnement affiche également son propre état d’allocation.  

## <a name="resolve-over-allocated-subscriptions"></a>Résoudre les abonnements sur-alloués
Il y a plusieurs façons de résoudre les surallocations :
- Contacter votre revendeur pour acheter des abonnements supplémentaires.
- Attendre jusqu’à la période de régularisation annuelle et payer les abonnements suralloués à ce moment. 
- Supprimer des attributions d’abonnement.  (Ceci n’empêchera pas la nécessité d’un paiement au moment de la régularisation annuelle, car la régularisation est basée sur le nombre maximal d’abonnements attribués à n’importe quel moment de l’année.)

## <a name="billing-and-true-up"></a>Facturation et régularisation
Si votre organisation a un Contrat Entreprise (EA), les administrateurs peuvent attribuer des abonnements sans les acheter, en les payant plus tard par le biais d’un processus de rapprochement appelé « régularisation ».  En cas de surutilisation, le nombre maximal d’abonnements attribués aux utilisateurs durant la « régularisation » est facturé à votre entreprise.  Cela est vrai même si le nombre actuel d’abonnements ne correspond plus au nombre maximal d’abonnements attribués au moment de la régularisation.  Pour en savoir plus sur le contrôle de l’utilisation maximum, consultez la rubrique [Utilisation maximum](maximum-usage.md).

> [!Important]
> Si des abonnements Visual Studio avec GitHub Enterprise sont attribués par des administrateurs d’abonnement Visual Studio alors qu’ils n’ont jamais été achetés, les administrateurs GitHub Enterprise au sein de l’organisation ne les voient pas. Pour vérifier que les abonnements GitHub Enterprise sont visibles, un achat comprenant **au moins** un abonnement Visual Studio Professional avec GitHub Enterprise ou Visual Studio Enterprise avec GitHub Enterprise doit être effectué à la première attribution des abonnements.
>
> Il appartient au client de vérifier qu’à chaque abonnement GitHub attribué correspond un abonnement Visual Studio avec GitHub attribué dans le portail Gérer afin de respecter les conditions de licence pour cet abonnement.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Découvrez-en plus sur la gestion des [abonnements Visual Studio avec GitHub Enterprise](assign-github.md).
- Pour obtenir de l’aide sur les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, contactez le [support des abonnements](https://visualstudio.microsoft.com/subscriptions/support/)Visual Studio.