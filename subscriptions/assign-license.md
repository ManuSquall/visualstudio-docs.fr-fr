---
title: Affecter des abonnements Visual Studio à des utilisateurs | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.openlocfilehash: 044cf4e9df3eb2ebf1d10aa8c08be804ca98f393
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467529"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Attribuer des licences dans le portail d’administration des abonnements Visual Studio
En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration pour affecter des abonnements à des utilisateurs individuels et à des groupes d’utilisateurs.

Pour les groupes d’utilisateurs, vous avez la possibilité de choisir la façon dont vous attribuez les abonnements.  
- Vous pouvez assigner un abonnement à la fois.
- Vous pouvez également télécharger rapidement et facilement des listes d’abonnés et leurs informations d’abonnement à l’aide de la fonctionnalité d' [Ajout en bloc](assign-license-bulk.md) .
- Si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez [utiliser des groupes de Azure AD pour affecter des abonnements](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) à des groupes d’utilisateurs.  


## <a name="add-a-single-subscriber"></a>Ajouter un seul abonné
Regardez la vidéo ou lisez ce qui suit pour savoir comment attribuer un abonnement Visual Studio à un nouvel utilisateur afin qu’il puisse accéder aux avantages de l’abonnement.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).
2. Pour attribuer une licence à un seul abonné Visual Studio, en haut du tableau, sélectionnez **Ajouter**, puis choisissez **abonné individuel**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter un seul abonné](_img/assign-license-add/add-subscriber-individual.png "Sélectionnez Ajouter, puis choisissez abonné individuel pour affecter un seul abonnement.")
3. Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, le champ **Nom** agit comme une fonction de recherche pour trouver les utilisateurs de votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cette personne, son nom, son e-mail de connexion et son e-mail de notification sont renseignés automatiquement.
   > [!div class="mx-imgBorder"]
   > ![Détails de l’abonné](_img/assign-license-add/subscriber-details.png "Entrez le nom de l’abonné et d’autres détails, ou choisissez parmi les membres du locataire.")

    > [!NOTE]
    > Pour que les membres d’un locataire Azure Active Directory soient visibles lorsque vous entrez un nom d’abonné, l’administrateur doit être membre du locataire. 


    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée dans la section **Paramètres de téléchargement**. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’aura pas accès aux téléchargements de logiciels.  L’accès aux clés de produit est également désactivé.  L’abonné aura toujours accès à tous les autres avantages inclus dans l’abonnement.
   > [!div class="mx-imgBorder"]
   > ! [Accès aux téléchargements] (Media/access-to-downloads.png « choisissez autoriser » pour permettre à l’abonné d’accéder aux téléchargements de logiciels».

    Pour ajouter vos propres notes de référence à l’abonnement, utilisez la section **Ajouter une référence**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter vos propres notes de référence à chaque abonnement](media/add-subscriber-reference-notes.png "Utilisez le champ de référence pour enregistrer les notes relatives à cet abonnement.")

    Après avoir sélectionné les options et entré les données de l’abonné, choisissez **Ajouter** en bas du menu volant **Ajouter l’abonné**.
   > [!div class="mx-imgBorder"]
   > ![Cliquez sur le bouton Ajouter](media/add-button.png "Sélectionnez Ajouter pour enregistrer les informations et attribuer l’abonnement à l’abonné.")

## <a name="resend-assignment-emails"></a>Renvoyer des e-mails d’attribution
Une fois que vous avez ajouté un abonné, un e-mail d’attribution est envoyé automatiquement au nouvel abonné avec des instructions supplémentaires. Vous pouvez renvoyer l’e-mail d’affectation à tout moment en sélectionnant l’abonné, puis en sélectionnant le bouton **renvoyer** dans le menu supérieur.  Pour renvoyer des e-mails à plusieurs utilisateurs, maintenez la touche **CTRL** enfoncée tout en sélectionnant les abonnés.  Lorsque vous sélectionnez le bouton **renvoyer** , une boîte de dialogue s’affiche pour vous demander de confirmer que vous souhaitez renvoyer à ces abonnés.  

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
- Vous avez un grand nombre d’utilisateurs à ajouter ?  Découvrez comment attribuer des abonnements à [plusieurs abonnés](assign-license-bulk.md).
- Besoin d'aide ?  Contactez la [prise en charge de l’administration et des abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).