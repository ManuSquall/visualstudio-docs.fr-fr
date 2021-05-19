---
title: Gérer les licences allouées dans les abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 05/18/2021
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent résoudre les abonnements sur-alloués
ms.openlocfilehash: 533ce71e8795e89bcb21fd437da6bea91db291f4
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973393"
---
# <a name="over-allocated-subscriptions"></a>Abonnements alloués
Les commandes sont parfois modifiées après l’ajout des abonnés. Le risque est que le nombre d’abonnements attribués dépasse le nombre de licences détenues par votre entreprise. C’est ce que l’on appelle « sur-allocation ».  

Pour afficher les allocations d’abonnement, cliquez sur l’icône en haut à gauche pour ouvrir le volet allocations.  

> [!NOTE]
> Les allocations excessives ne sont pas autorisées dans les programmes de licence Open.  En outre, d’autres programmes peuvent afficher ces informations différemment dans le portail.
>
> [!div class="mx-imgBorder"]
> ![Notification de surutilisation d’abonnements](_img/over-claimed/over-claimed-alert.png "Le nombre de surallocations est indiqué dans la vue d’ensemble et est représenté par la barre hachée sur le graphique pour chaque type d’abonnement.")

Notez que l’affichage utilise une barre hachée pour indiquer des abonnements sur-alloués.  Le nombre de surallocations pour tous les types d’abonnements est inclus dans la section vue d’ensemble en haut, et chaque niveau d’abonnement affiche également son propre état d’allocation.  

## <a name="receive-notifications-when-over-allocations-occur"></a>Recevoir des notifications lorsque des allocations excessives se produisent
Vous pouvez désigner une adresse de messagerie pour recevoir des notifications lorsque des surallocations se produisent, et définir un seuil qui doit être dépassé avant l’envoi des notifications.  En savoir plus sur la [définition des préférences pour vos contrats](admin-preferences.md) dans le portail d’administration.

## <a name="resolve-over-allocated-subscriptions"></a>Résoudre les abonnements sur-alloués
Il existe plusieurs façons de résoudre des allocations excessives :
- Contacter votre revendeur pour acheter des abonnements supplémentaires.
- Patientez jusqu’à la période de cumul annuel et payez les abonnements suralloués à ce stade. 
- Supprimer des attributions d’abonnement.  (Ceci n’empêchera pas la nécessité d’un paiement au moment de la régularisation annuelle, car la régularisation est basée sur le nombre maximal d’abonnements attribués à n’importe quel moment de l’année.)

## <a name="billing-and-true-up"></a>Facturation et régularisation
Si votre organisation a un Contrat Entreprise (EA), les administrateurs peuvent attribuer des abonnements sans les acheter, en les payant plus tard par le biais d’un processus de rapprochement appelé « régularisation ».  Lorsque vous surallouez, votre organisation est facturée pour le nombre maximal d’abonnements attribués aux utilisateurs lors de la « vraie ».  Cela est vrai même si le nombre actuel d’abonnements ne correspond plus au nombre maximal d’abonnements attribués au moment de la régularisation.  Pour en savoir plus sur le contrôle de l’utilisation maximum, consultez la rubrique [Utilisation maximum](maximum-usage.md).


## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- En savoir plus sur la gestion des [abonnements Visual Studio avec Github Enterprise](assign-github.md).
- Pour obtenir de l’aide sur les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, contactez le [support des abonnements](https://aka.ms/vsadminhelp)Visual Studio.