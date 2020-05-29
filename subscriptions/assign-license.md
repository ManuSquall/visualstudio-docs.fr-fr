---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.openlocfilehash: a90d6f3fec1f619cda397788c130f7514307effd
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183468"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Attribuer des licences dans le portail d’administration des abonnements Visual Studio
En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration pour attribuer des abonnements à des utilisateurs individuels ou à des groupes d’utilisateurs.

Pour les groupes d’utilisateurs, vous avez la possibilité de choisir la façon dont vous attribuez les abonnements.  
- Vous pouvez assigner un abonnement à la fois.
- Vous pouvez également télécharger rapidement et facilement des listes d’abonnés et leurs informations d’abonnement à l’aide de la fonctionnalité d' [Ajout en bloc](assign-license-bulk.md) .
- Si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez [utiliser des groupes de Azure AD pour affecter des abonnements](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions) à des groupes d’utilisateurs.  


## <a name="add-a-single-subscriber"></a>Ajouter un seul abonné
Voici comment affecter un abonnement Visual Studio à un nouvel utilisateur afin qu’il puisse accéder aux avantages de l’abonnement.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).
2. Pour attribuer une licence à un seul abonné Visual Studio, en haut du tableau, sélectionnez **Ajouter**, puis choisissez **abonné individuel**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter un seul abonné](_img/assign-license-add/add-subscriber-individual.png)
3. Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, le champ **Nom** agit comme une fonction de recherche pour trouver les utilisateurs de votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cette personne, son nom, son e-mail de connexion et son e-mail de notification sont renseignés automatiquement.
   > [!div class="mx-imgBorder"]
   > ![Détails de l’abonné](_img/assign-license-add/subscriber-details.png)

    > [!NOTE]
    > Pour que les membres d’un locataire Azure Active Directory soient visibles lorsque vous entrez un nom d’abonné, l’administrateur doit être membre du locataire. 


    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée dans la section **Paramètres de téléchargement**. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’aura pas accès aux téléchargements de logiciels.  L’accès aux clés de produit est également désactivé.  L’abonné aura toujours accès à tous les autres avantages inclus dans l’abonnement.
   > [!div class="mx-imgBorder"]
   > ![Accéder aux téléchargements](media/access-to-downloads.png)

    Pour ajouter vos propres notes de référence à l’abonnement, utilisez la section **Ajouter une référence**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter vos propres notes de référence à chaque abonnement](media/add-subscriber-reference-notes.png)

    Après avoir sélectionné les options et entré les données de l’abonné, choisissez **Ajouter** en bas du menu volant **Ajouter l’abonné**.
   > [!div class="mx-imgBorder"]
   > ![Choisir le bouton Ajouter](media/add-button.png)

## <a name="resend-assignment-emails"></a>Renvoyer des e-mails d’attribution
Une fois que vous avez ajouté un abonné, un e-mail d’attribution est envoyé automatiquement au nouvel abonné avec des instructions supplémentaires. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **renvoyer** dans le menu supérieur.  Pour renvoyer des e-mails à plusieurs utilisateurs, maintenez la touche **CTRL** enfoncée tout en sélectionnant les abonnés.  Lorsque vous cliquez sur le bouton **renvoyer** , une boîte de dialogue s’affiche pour vous demander de confirmer que vous souhaitez renvoyer à ces abonnés.  

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
- Vous avez un grand nombre d’utilisateurs à ajouter ?  Découvrez comment attribuer des abonnements à [plusieurs abonnés](assign-license-bulk.md).
- Besoin d'aide ?  Contactez la [prise en charge de l’administration et des abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).


