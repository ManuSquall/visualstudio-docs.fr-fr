---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 6f0bbded7682bd8f7162ae415c6c83711df04a04
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931231"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Attribuer des licences dans le portail d’administration des abonnements Visual Studio

En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration pour attribuer des abonnements à des utilisateurs spécifiques ou à des groupes d’utilisateurs.

Pour les groupes d’utilisateurs, vous pouvez leur attribuer des abonnements (un à la fois) ou utiliser la fonctionnalité **Ajouter en bloc** pour charger rapidement et facilement des listes d’abonnés avec leurs informations d’abonnement.

## <a name="individual-assignments"></a>Attributions individuelles

Voici comment attribuer une licence d’abonnement Visual Studio à un nouvel utilisateur afin qu’il ait accès aux avantages associés.

1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).

2. Pour attribuer une licence à un seul abonné Visual Studio, sélectionnez **Ajouter** en haut du tableau.
   > [!div class="mx-imgBorder"]
   > ![Ajouter un seul abonné](media/add-single-subscriber.png)

3. Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, vous pouvez utiliser ce champ pour rechercher des utilisateurs dans votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cet utilisateur, son nom, son adresse e-mail de connexion et son adresse e-mail de notification sont automatiquement renseignés.
   > [!div class="mx-imgBorder"]
   > ![Ajouter une nouvelle adresse e-mail de notification](media/add-new-subscriber-notification-email.png)

    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée dans la section **Paramètres de téléchargement**. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’a pas accès aux téléchargements de logiciels, mais il garde l’accès à tous les autres avantages inclus dans son abonnement.
   > [!div class="mx-imgBorder"]
   > ![Accéder aux téléchargements](media/access-to-downloads.png)

    Pour changer la langue dans laquelle l’abonné reçoit des informations, utilisez la section **Préférences de communication**.
   > [!div class="mx-imgBorder"]
   > ![Changer la langue à utiliser pour l’envoi d’e-mails de notification](media/change-subscriber-communication-preference.png)

    Pour ajouter vos propres notes de référence à l’abonnement, utilisez la section **Ajouter une référence**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter vos propres notes de référence à chaque abonnement](media/add-subscriber-reference-notes.png) 

    Après avoir sélectionné les options et entré les données de l’abonné, choisissez **Ajouter** en bas du menu volant **Ajouter l’abonné**.
   > [!div class="mx-imgBorder"]
   > ![Choisir le bouton Ajouter](media/add-button.png)

4. Une fois que vous avez ajouté l’abonné, un e-mail d’attribution, contenant des instructions supplémentaires, est automatiquement envoyé au nouvel abonné. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **Renvoyer** dans le menu supérieur.
   > [!div class="mx-imgBorder"]
   > ![Renvoyer un e-mail d’activation à n’importe quel utilisateur ou à plusieurs utilisateurs chaque fois que vous le souhaitez](media/resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Attributions en bloc

1. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **Gérer les abonnés**. Dans le ruban du haut, cliquez sur **Ajouter en bloc**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter plusieurs abonnés](media/add-multiple-subscribers.png)

2. L’attribution en bloc utilise un modèle Microsoft Excel pour charger les abonnés. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle.
   > [!div class="mx-imgBorder"]
   > ![Télécharger le modèle Excel pour charger plusieurs abonnés](media/download-template-upload-subscribers.png)
   > 
   > [!NOTE]
   > Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

3. Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. (Le champ *Référence* est facultatif.) Enregistrez le fichier localement une fois que vous avez terminé.

   Pour faciliter le chargement, respectez les bonnes pratiques suivantes :

    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après les champs de formulaire.
    - Assurez-vous que les noms d’utilisateur ne contiennent pas d’espace superflu dans les noms ou prénoms composés (par exemple, si une personne porte le prénom composé « Maggie May », il doit être entré sous la forme « MaggieMay », car le système ne supprime pas l’espace superflu).

4. Revenez au portail d’administration des abonnements Visual Studio. Dans la boîte de dialogue permettant de **charger plusieurs abonnés**, cliquez sur **Parcourir**.
   > [!div class="mx-imgBorder"]
   > ![Accéder à votre modèle enregistré pour charger plusieurs abonnés](media/bulk-add-browse-saved-template.png)

5. Accédez au fichier Excel que vous avez enregistré, puis cliquez sur **OK**.
   > [!div class="mx-imgBorder"]
   > ![Charger le modèle Excel pour charger plusieurs abonnés](media/bulk-upload-subscribers.png)

    Une boîte de dialogue de progression du chargement s’affiche.

    Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.
   > [!div class="mx-imgBorder"]
   > ![Message d’erreur si le chargement de plusieurs abonnés échoue](media/bulk-add-template-failed.png)

    Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.
   > [!div class="mx-imgBorder"]
   > ![Message de confirmation si le chargement de plusieurs abonnés réussit](media/bulk-add-template-success.png)
