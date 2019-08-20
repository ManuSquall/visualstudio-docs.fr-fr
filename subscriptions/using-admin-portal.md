---
title: Bien démarrer avec le portail d’administration des abonnements | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Découvrez comment bien démarrer avec la gestion des abonnements Visual Studio de votre organisation via le portail d’administration des abonnements.
ms.openlocfilehash: f3b11a0a0977fff8a6c89f565adffb1cac49e2ad
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605719"
---
# <a name="get-started-with-the-visual-studio-subscriptions-administration-portal"></a>Bien démarrer avec le portail d’administration des abonnements Visual Studio
Quand vous utilisez le portail d’administration des abonnements Visual Studio, gardez à l’esprit les points suivants :
- **Les abonnements Visual Studio sont fournis avec une licence par utilisateur.** Chaque abonné peut utiliser les logiciels sur un nombre illimité d’ordinateurs à des fins de développement et de test.
- **Attribuez un seul niveau d’abonnement à chaque abonné**, en fonction de l’abonnement Visual Studio que votre organisation a acheté. Si des abonnés ont plusieurs niveaux d’abonnement, modifiez leurs paramètres de sorte qu’un seul niveau d’abonnement leur soit attribué.
- **Le niveau d’abonnement d’un abonné doit être mis à jour** quand l’abonnement est mis à niveau (après l’achat d’une licence de niveau supérieur) ou renouvelé à un niveau inférieur.
- **Ne partagez pas d’abonnements entre abonnés.** Les abonnements doivent être attribués à des personnes nommées.  L’attribution d’abonnements à des équipes n’est pas autorisée.  Vous devez attribuer un abonnement à chaque personne qui utilise la totalité ou une partie des avantages de l’abonnement (logiciels de développement et de test, Microsoft Azure, eLearning, etc.).

## <a name="access-to-the-portal"></a>Accéder au portail
Si vous êtes le contact principal ou l’interlocuteur pour les notifications sur le contrat de votre organisation, votre accès au portail est provisionné automatiquement lors de la configuration de votre contrat de licence en volume. Vous recevez un e-mail de bienvenue envoyé par le système qui indique l’adresse e-mail à utiliser pour se connecter au portail. Une fois que vous êtes connecté, vous êtes configuré automatiquement configuré en tant que super administrateur, et vous pouvez commencer à gérer les abonnements et d’autres administrateurs. 

## <a name="administrator-roles"></a>Rôles d’administrateur
Dans le nouveau portail d’administration des abonnements Visual Studio, deux rôles sont disponibles pour les clients de licence en volume. Ces rôles s’apparentent au rôle Contact principal/Destinataire des avis et au rôle Gestionnaire d’abonnements disponibles dans VLSC.

**Super administrateurs :** au moment de la création d’une organisation, le contact principal ou le destinataire des notifications devient super administrateur par défaut. Le contact principal ou l’interlocuteur pour les notifications peut choisir d’affecter des super administrateurs ou des administrateurs supplémentaires. Un super administrateur peut ajouter et supprimer d’autres administrateurs, ainsi que des abonnés. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en garder au minimum deux pour des raisons de sécurité.

**Administrateurs :** un administrateur peut uniquement être créé par un super administrateur. Il peut gérer les abonnés dans les contrats que le super administrateur leur attribue.

## <a name="the-subscribers-page"></a>Page Abonnés
Une fois que vous avez attribué les abonnements, l’onglet Abonnés fournit des informations détaillées suivantes sur les abonnés :
- Nom et prénom des abonnés.
- Leur adresse e-mail.
- Niveau d’abonnement qui leur a été attribué.
- Date d’attribution de leur abonnement.
- Date d’expiration de leur abonnement.
- Texte descriptif facultatif.
- Indication de l’activation ou de la désactivation des téléchargements pour les abonnés.
- Pays dans lequel ils sont situés.
- Langue choisie pour l’e-mail de communication d’attribution envoyé par le portail d’administration.
- Champ facultatif indiquant une adresse e-mail pour les communications différente de celle pour la connexion.

Sur le côté gauche de cette page, vous pouvez voir des informations supplémentaires sur le nombre de licences d’abonnement achetées, attribuées et encore disponibles dans votre organisation pour chaque contrat.
> [!div class="mx-imgBorder"]
> ![Page Abonnés dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/subscribers-page.png)

## <a name="the-details-page"></a>Page Détails
Pour obtenir plus d’informations sur le contrat affiché, sélectionnez l’onglet Détails. Cet onglet indique le statut du contrat, le compte d’achat, des détails sur l’organisation, les super administrateurs et d’autres informations pertinentes.
> [!div class="mx-imgBorder"]
> ![Page Détails dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/details-page.png)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les responsabilités des administrateurs :
- [Vue d’ensemble des responsabilités des administrateurs](admin-responsibilities.md)
- [Inventaire de l’environnement de préproduction](admin-inventory.md)
- [Gérer de grandes équipes et des fournisseurs externes](manage-teams.md)
- [Suivre les affectations d’utilisateurs et traiter les commandes](assignments-orders.md)
- Utiliser le rapport [Utilisation maximale](maximum-usage.md) pour suivre les engagements d’achat
