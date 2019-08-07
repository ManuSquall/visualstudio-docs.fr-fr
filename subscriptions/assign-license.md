---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.openlocfilehash: 8125c5cbad2ff44dabbf1b0c5014c313d75d2e71
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604709"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Attribuer des licences dans le portail d’administration des abonnements Visual Studio
En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration pour attribuer des abonnements à des utilisateurs individuels ou à des groupes d’utilisateurs.

Pour les groupes d’utilisateurs, vous pouvez leur attribuer des abonnements (un à la fois) ou utiliser la fonctionnalité [Ajouter en bloc](assign-license-bulk.md) pour charger rapidement et facilement des listes d’abonnés avec leurs informations d’abonnement.

## <a name="add-a-single-subscriber"></a>Ajouter un seul abonné
Voici comment attribuer une licence d’abonnement Visual Studio à un nouvel utilisateur afin qu’il ait accès aux avantages associés.

1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).
2. Pour attribuer une licence à un seul abonné Visual Studio, sélectionnez **Ajouter** en haut du tableau.
   > [!div class="mx-imgBorder"]
   > ![Ajouter un seul abonné](media/add-single-subscriber.png)
3. Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, le champ **Nom** agit comme une fonction de recherche pour trouver les utilisateurs de votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cette personne, son nom, son e-mail de connexion et son e-mail de notification sont renseignés automatiquement.
   > [!div class="mx-imgBorder"]
   > ![Détails de l’abonné](_img/assign-license-add/subscriber-details.png)

    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée dans la section **Paramètres de téléchargement**. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’a pas accès aux téléchargements de logiciels, mais il garde l’accès à tous les autres avantages inclus dans son abonnement.
   > [!div class="mx-imgBorder"]
   > ![Accéder aux téléchargements](media/access-to-downloads.png)

       If you'd like to add your own reference notes to the subscription, you can do so in the **Add reference** section.
   > [!div class="mx-imgBorder"]
   > ![Ajouter vos propres notes de référence à chaque abonnement](media/add-subscriber-reference-notes.png)

    Après avoir sélectionné les options et entré les données de l’abonné, choisissez **Ajouter** en bas du menu volant **Ajouter l’abonné**.
   > [!div class="mx-imgBorder"]
   > ![Choisir le bouton Ajouter](media/add-button.png)

4. Une fois que vous avez ajouté l’abonné, un e-mail d’attribution, contenant des instructions supplémentaires, est automatiquement envoyé au nouvel abonné. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **Renvoyer** dans le menu supérieur.

## <a name="next-steps"></a>Étapes suivantes
- Vous avez un grand nombre d’utilisateurs à ajouter ?  Découvrez comment attribuer des abonnements à [plusieurs abonnés](assign-license-bulk.md).
- Vous avez besoin d'aide ?  Contactez le [Support technique sur l’administration et les abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

