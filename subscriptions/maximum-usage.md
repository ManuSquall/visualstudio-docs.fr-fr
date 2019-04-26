---
title: Utilisation de la fonctionnalité d’utilisation maximale dans le portail d’administration
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Découvrir comment afficher le nombre maximal d’abonnements attribués dans le portail d’administration
searchscope: VS Subscription
ms.openlocfilehash: c263c610b140d3662cb17ba9f2c3d3f1a1907ab7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965401"
---
# <a name="using-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Utilisation de la fonctionnalité d’utilisation maximale pour suivre le nombre d’abonnements attribués

Une nouvelle fonctionnalité du portail d’administration des abonnements Visual Studio vous permet de suivre le nombre d’abonnements que vous avez achetés et attribués. Elle permet également d’identifier le nombre maximal d’abonnements de chaque niveau que vous avez attribués au cours de l’année précédente et pendant la durée de votre ou vos contrats. 

## <a name="viewing-maximum-usage"></a>Affichage de l’utilisation maximale

Pour voir le nombre maximal d’abonnements attribués pour tout contrat et niveau d’abonnement :

1. Sélectionnez le contrat que vous voulez voir dans la liste déroulante en haut à gauche du portail. (Si vous avez un seul contrat, celui-ci est peut-être déjà sélectionné.)

2. Cliquez sur l’onglet **Maximum Usage** (Utilisation maximale).  
    > [!div class="mx-imgBorder"]
    > ![Menu Maximum Usage](_img/maximum-usage/maximum-usage-menu.png)

3. La fenêtre « Maximum Usage Summary » (Récapitulatif de l’utilisation maximale) apparaît, et le nombre maximal d’abonnements que vous avez attribués au cours de l’année précédente pour chaque niveau est affiché, avec la date à laquelle vous avez atteint ce pic.  Si vous avez atteint ce pic plusieurs fois, la première fois où vous l’avez atteint est affichée. 
    > [!div class="mx-imgBorder"]
    > ![Maximum Usage Summary](_img/maximum-usage/maximum-usage-summary.png)

4. Pour voir le nombre maximal d’abonnements attribués pendant la durée du contrat, cliquez sur l’onglet **Full-Term** (Durée complète).

## <a name="viewing-assignment-history"></a>Affichage de l’historique des attributions

En plus de voir le nombre maximal d’attributions pour chaque niveau d’abonnement, vous pouvez voir un compte actuel de l’activité sur le contrat, notamment les achats et les attributions, en cliquant sur le bouton **Export full report** (Exporter le rapport complet).  

> [!div class="mx-imgBorder"]
> ![Rapport complet sur l’utilisation maximale](_img/maximum-usage/maximum-usage-full-report.png)

Pour chaque niveau d’abonnement, le rapport affiche la date à laquelle vous avez atteint un nouveau niveau d’attribution maximal et le nombre d’abonnements que vous avez achetés à compter de cette date. Cela vous permet de voir facilement toutes les dates auxquelles vous aviez des surutilisations.  

Par exemple, dans le tableau ci-dessus, vous pouvez voir que le 13 décembre 2018, le contrat comprenait 123 abonnements Visual Studio Enterprise et 120 étaient attribués.  Le 8 janvier 2019, un abonnement supplémentaire a été attribué, portant le total à 121.  Le lendemain, six autres abonnements ont été attribués, et quatre autres abonnements ont été ajoutés au contrat pour couvrir les nouvelles attributions.  

## <a name="frequently-asked-questions"></a>FAQ
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>Q : En quoi les informations contenues dans Maximum Usage sont-elles différentes des informations relatives aux attributions disponibles dans la section « Overview » sur le côté gauche du portail ?

R :  Les informations contenues dans la vue d’ensemble montrent les attributions actuelles et les abonnements disponibles pour chaque niveau d’abonnement.  Elles peuvent être très différentes du nombre maximal d’abonnements attribués pour le contrat à tout moment.  La fonctionnalité Maximum Usage vous permet de voir quand le nombre maximal des niveaux d’attributions a été atteint et quels étaient ces niveaux.  Cette distinction est importante, étant donné que la facturation des abonnements pendant la régularisation est basée sur le nombre maximal d’abonnements attribués à tout moment. 

## <a name="next-steps"></a>Étapes suivantes
Si vous avez des questions sur les attributions d’abonnements ou d’autres aspects du portail d’administration, contactez https://visualstudio.microsoft.com/subscriptions/support/ pour obtenir de l’aide. 