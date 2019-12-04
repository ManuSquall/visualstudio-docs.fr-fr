---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.openlocfilehash: 8785d4d4253fa3217341c8200a94dab923ae4a5f
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797366"
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

## <a name="resend-assignment-emails"></a>Renvoyer des e-mails d’attribution
Une fois que vous avez ajouté un abonné, un e-mail d’attribution est envoyé automatiquement au nouvel abonné avec des instructions supplémentaires. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **renvoyer** dans le menu supérieur.  Pour renvoyer des e-mails à plusieurs utilisateurs, maintenez la touche **CTRL** enfoncée tout en sélectionnant les abonnés.  Lorsque vous cliquez sur le bouton **renvoyer** , une boîte de dialogue s’affiche pour vous demander de confirmer que vous souhaitez renvoyer à ces abonnés.  

## <a name="next-steps"></a>Étapes suivantes :
- Vous avez un grand nombre d’utilisateurs à ajouter ?  Découvrez comment attribuer des abonnements à [plusieurs abonnés](assign-license-bulk.md).
- Vous avez besoin d'aide ?  Contactez le [Support technique sur l’administration et les abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

