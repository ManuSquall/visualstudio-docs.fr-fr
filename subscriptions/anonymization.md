---
title: Anonymisation des données des abonnés Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: Découvrez comment les données des abonnés sont anonymisées quand l’accès aux abonnements est perdu.
searchscope: VS Subscription
ms.openlocfilehash: a4249aa2520df6e9c1870fec121de2fdb2135308
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842544"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymisation des informations sur les abonnés Visual Studio

Quand un événement (par exemple l’expiration d’un abonnement ou la suppression du compte de connexion d’un abonné) bloque l’utilisation d’un abonnement par un abonné, les informations personnelles de l’utilisateur, telles que son nom et son compte de connexion, sont brouillées afin de les rendre inutilisables.  Le but est de protéger les informations personnelles de l’abonné.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Quand l’anonymisation a-t-elle lieu ?

Les événements qui rendent un abonnement inutilisable par un abonné déclenchent l’anonymisation.  La vitesse à laquelle l’anonymisation se produit varie en fonction du type d’abonnement et de l’événement déclencheur. Pour plus d’informations, consultez le tableau ci-dessous.

| Type d’abonnement                                                                                                                       | Événement déclenchant l’anonymisation                                                                                                     | Délai au-delà duquel l’anonymisation a lieu |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | L’abonné annule son adhésion au programme ou n’accepte pas les conditions d’utilisation                                    | 30 jours               |
| Abonnements Visual Studio achetés par le biais du Microsoft Store (vente au détail)                                                                      | L’abonnement arrive à expiration ou n’est pas activé                                                                   | 360 jours                  |
| Abonnements Visual Studio acquis par le biais du programme de licence en volume, Visual Studio Marketplace (abonnements cloud) ou programmes tels que MPN | L’abonnement arrive à expiration ou n’est affecté à aucun utilisateur                                                          | 180 jours                  |
| Tous les abonnements                                                                                                                       | Un compte Azure Active Directory ou un compte Microsoft (MSA) utilisé pour se connecter à l’abonnement est fermé | Immédiatement               |
| Tous les abonnements                                                                                                                       | Un abonné est supprimé du locataire qui est associé au compte Azure Active Directory                                | Immédiatement               |

## <a name="faq"></a>FAQ

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Q :  Quand les informations personnelles d’un abonné sont anonymisées, celui-ci perd-il l’accès à l’abonnement ?
R :  Non.  L’anonymisation a lieu en réponse à un événement qui entraîne la perte d’accès à l’abonnement, mais elle n’entraîne pas l’absence d’accès.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Q :  Je suis chargé de l’administration des abonnements de mon organisation.  Si les informations de l’un de mes abonnés sont anonymisées, cet abonnement peut-il être réaffecté à un autre utilisateur ?
R :  Oui. Tant que l’abonnement n’est pas arrivé à expiration, il peut être réaffecté à un autre abonné.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment empêcher l’anonymisation en [établissant une liaison entre les identités MSA et AAD](/azure/active-directory/b2b/add-users-administrator).
