---
title: Utiliser la fonctionnalité d’utilisation maximale dans le portail d’administration
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Découvrir comment afficher le nombre maximal d’abonnements attribués dans le portail d’administration
ms.openlocfilehash: 368ca1ad0373267e9753ab223c2e200cbc87f1e0
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491722"
---
# <a name="use-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Utiliser la fonctionnalité d’utilisation maximale pour suivre le nombre d’abonnements affectés
Une nouvelle fonctionnalité du portail d’administration des abonnements Visual Studio vous permet de suivre le nombre d’abonnements que vous avez achetés et attribués. Elle permet également d’identifier le nombre maximal d’abonnements de chaque niveau que vous avez attribués au cours de l’année précédente et pendant la durée de votre ou vos contrats. 

## <a name="view-your-maximum-usage"></a>Voir votre utilisation maximale
Pour voir le nombre maximal d’abonnements attribués pour tout contrat et niveau d’abonnement :
1. Sélectionnez le contrat que vous voulez voir dans la liste déroulante en haut à gauche du portail. (Si vous avez un seul contrat, celui-ci est peut-être déjà sélectionné.)
2. Cliquez sur l’onglet **Maximum Usage** (Utilisation maximale).  
    > [!div class="mx-imgBorder"]
    > ![Menu Maximum Usage](_img/maximum-usage/maximum-usage-menu.png)
3. La fenêtre « Maximum Usage Summary » (Récapitulatif de l’utilisation maximale) apparaît, et le nombre maximal d’abonnements que vous avez attribués au cours de l’année précédente pour chaque niveau est affiché, avec la date à laquelle vous avez atteint ce pic.  Si vous avez atteint ce pic plusieurs fois, la première fois où vous l’avez atteint est affichée. 
    > [!div class="mx-imgBorder"]
    > ![Maximum Usage Summary](_img/maximum-usage/maximum-usage-summary.png)
4. Pour voir le nombre maximal d’abonnements attribués pendant la durée du contrat, cliquez sur l’onglet **Full-Term** (Durée complète).

## <a name="view-your-assignment-history"></a>Voir votre historique d’affectations
En plus de voir le nombre maximal d’attributions pour chaque niveau d’abonnement, vous pouvez voir un compte actuel de l’activité sur le contrat, notamment les achats et les attributions, en cliquant sur le bouton **Export full report** (Exporter le rapport complet).  

> [!div class="mx-imgBorder"]
> ![Rapport complet sur l’utilisation maximale](_img/maximum-usage/maximum-usage-full-report.png)

Pour chaque niveau d’abonnement, le rapport affiche la date à laquelle vous avez atteint un nouveau niveau d’attribution maximal et le nombre d’abonnements que vous avez achetés à compter de cette date. Cela vous permet de voir facilement toutes les dates auxquelles vous aviez des surutilisations.  

Par exemple, dans le tableau ci-dessus, vous pouvez voir que le 13 décembre 2018, le contrat comprenait 123 abonnements Visual Studio Enterprise et 120 étaient attribués.  Le 8 janvier 2019, un abonnement supplémentaire a été attribué, portant le total à 121.  Le lendemain, six autres abonnements ont été attribués, et quatre autres abonnements ont été ajoutés au contrat pour couvrir les nouvelles attributions.  

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>Q : comment les informations de l’utilisation maximale diffèrent-elles des informations d’affectation disponibles dans la section « vue d’ensemble » sur le côté gauche du portail ?
R : les informations de la vue d’ensemble indiquent les attributions *actuelles* et les abonnements disponibles pour chaque niveau d’abonnement.  Elles peuvent être très différentes du nombre maximal d’abonnements attribués pour le contrat au cours de l’année en cours ou de la durée du contrat.  La fonctionnalité utilisation maximale vous permet de voir à quel moment le nombre maximal d’affectations a été atteint et les niveaux.  Il s’agit d’une distinction importante, car la facturation des abonnements durant la régularisation est basée sur le nombre maximal d’abonnements affectés à tout moment de l’année. 

## <a name="resources"></a>Ressources
- [Livre blanc sur la gestion des licences Visual Studio](https://aka.ms/vslicensing)
- [Prise en charge des abonnements et de l’administration de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Conditions du programme de licence en volume](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Étapes suivantes :
- Si vous avez des questions sur les attributions d’abonnements ou d’autres aspects du portail d’administration, contactez https://visualstudio.microsoft.com/subscriptions/support/ pour obtenir de l’aide. 
- Découvrez plus d’informations sur la procédure à suivre si vous attribuez plus d’abonnements que ce que avez acheté : ceci est désigné sous le nom de [surallocation](handle-overclaimed-license.md).
