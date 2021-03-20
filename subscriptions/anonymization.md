---
title: Anonymisation des données des abonnés Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Découvrez comment les données des abonnés sont anonymisées quand l’accès aux abonnements est perdu.
ms.openlocfilehash: 2a3d55824db1c90ff0868dda6d398e8c0e9a53d7
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757605"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymisation des informations sur les abonnés Visual Studio
Quand un événement (par exemple l’expiration d’un abonnement ou la suppression du compte de connexion d’un abonné) bloque l’utilisation d’un abonnement par un abonné, les informations personnelles de l’utilisateur, telles que son nom et son compte de connexion, sont brouillées afin de les rendre inutilisables.  Le but est de protéger les informations personnelles de l’abonné.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Quand l’anonymisation a-t-elle lieu ?
Les événements qui rendent un abonnement inutilisable par un abonné déclenchent l’anonymisation.  La vitesse à laquelle l’anonymisation se produit varie en fonction du type d’abonnement et de l’événement déclencheur. Pour plus d’informations, consultez le tableau ci-après.

| Type d'abonnement                                                                                                                       | Événement déclenchant l’anonymisation                                                                                                     | Délai au-delà duquel l’anonymisation a lieu |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | L’abonné annule son adhésion au programme ou n’accepte pas les conditions d’utilisation                                    | 30 jours               |
| Abonnements Visual Studio achetés par le biais du Microsoft Store (vente au détail)                                                                      | L’abonnement arrive à expiration ou n’est pas activé                                                                   | 360 jours                  |
| Abonnements Visual Studio acquis par le biais du programme de licence en volume, Visual Studio Marketplace (abonnements cloud) ou programmes tels que MPN | L’abonnement arrive à expiration ou n’est affecté à aucun utilisateur                                                          | 180 jours                  |
| Tous les abonnements                                                                                                                       | Un compte Azure Active Directory ou un compte Microsoft (MSA) utilisé pour se connecter à l’abonnement est fermé | Immédiatement               |
| Tous les abonnements                                                                                                                       | Un abonné est supprimé du locataire qui est associé au compte Azure Active Directory                                | Immédiatement               |

## <a name="faq"></a>Questions fréquentes (FAQ)
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Q : Quand les données personnelles d’un abonné sont anonymisées, celui-ci perd-il l’accès à l’abonnement ?
R : Non.  L’anonymisation a lieu en réponse à un événement qui entraîne la perte d’accès à l’abonnement, mais elle n’entraîne pas l’absence d’accès.

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Q : je suis administrateur pour les abonnements de mon organisation.  Si les informations de l’un de mes abonnés sont anonymisées, cet abonnement peut-il être réaffecté à un autre utilisateur ?
R : Oui.  Les abonnements peuvent être réaffectés si ces critères sont satisfaits :
- L’abonnement n’a pas expiré
- Un minimum de 90 jours se sont écoulés depuis la dernière attribution de l’abonnement à un abonné.  Par exemple, si un abonnement a été attribué à un abonné le 1er juin, il ne peut pas être réaffecté jusqu’au 30 août.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Q : Comment puis-je empêcher l’anonymisation due à la suppression d’une adresse de messagerie de connexion ?
R : il existe deux façons d’éviter ce problème :
- Déployez un système de gestion d’identité unique, AAD ou MSA mais pas les deux  
- Associez les identités AAD et MSA par le biais du locataire. 

## <a name="support-resources"></a>Ressources de support
- Pour obtenir de l’aide sur les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, consultez [prise en charge des abonnements](https://aka.ms/vssubscriberhelp)Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Découvrez comment empêcher l’anonymisation en [associant les identités MSA et AAD](/azure/active-directory/b2b/add-users-administrator).