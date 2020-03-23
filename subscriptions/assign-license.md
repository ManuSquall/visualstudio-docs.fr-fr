---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.openlocfilehash: 3d444f930d1fab166d437911b5609caf75cad09e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78263307"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Attribuer des licences dans le portail d’administration des abonnements Visual Studio
En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration pour attribuer des abonnements à des utilisateurs individuels ou à des groupes d’utilisateurs.

Pour les groupes d’utilisateurs, vous avez le choix pour la façon dont vous assignez des abonnements.  
- Vous pouvez attribuer des abonnements un à la fois.
- Vous pouvez également télécharger rapidement et facilement des listes d’abonnés et leurs informations d’abonnement à l’aide de la fonctionnalité [Bulk add.](assign-license-bulk.md)
- Si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez utiliser les groupes Azure AD pour affecter des abonnements à des groupes d’utilisateurs.  (Cette fonctionnalité est déployée par étapes et peut ne pas être immédiatement disponible pour votre organisation.)


## <a name="add-a-single-subscriber"></a>Ajouter un seul abonné
Voici comment attribuer un abonnement Visual Studio à un nouvel utilisateur afin qu’il puisse accéder aux avantages d’abonnement.

1. Connectez-vous au [portail administratif](https://manage.visualstudio.com).
2. Pour attribuer une licence à un seul abonné Visual Studio, en haut de la table, **sélectionnez Ajouter,** puis choisissez **un abonné individuel**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter un seul abonné](_img/assign-license-add/add-subscriber-individual.png)
3. Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, le champ **Nom** agit comme une fonction de recherche pour trouver les utilisateurs de votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cette personne, son nom, son e-mail de connexion et son e-mail de notification sont renseignés automatiquement.
   > [!div class="mx-imgBorder"]
   > ![Détails de l’abonné](_img/assign-license-add/subscriber-details.png)

    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée dans la section **Paramètres de téléchargement**. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’a pas accès aux téléchargements de logiciels, mais il garde l’accès à tous les autres avantages inclus dans son abonnement.
   > [!div class="mx-imgBorder"]
   > ![Accéder aux téléchargements](media/access-to-downloads.png)

    Pour ajouter vos propres notes de référence à l’abonnement, utilisez la section **Ajouter une référence**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter vos propres notes de référence à chaque abonnement](media/add-subscriber-reference-notes.png)

    Après avoir sélectionné les options et entré les données de l’abonné, choisissez **Ajouter** en bas du menu volant **Ajouter l’abonné**.
   > [!div class="mx-imgBorder"]
   > ![Choisir le bouton Ajouter](media/add-button.png)

## <a name="resend-assignment-emails"></a>Réendez les e-mails d’affectation
Après avoir ajouté un abonné, un e-mail d’affectation sera automatiquement envoyé au nouvel abonné avec d’autres instructions. Vous pouvez envoyer l’e-mail d’affectation à nouveau à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **Resend** dans le menu supérieur.  Pour renvoyer des e-mails à plusieurs utilisateurs, maintenez la clé **Ctrl** tout en sélectionnant les abonnés.  Lorsque vous cliquez sur le bouton **Resend,** vous verrez un dialogue vous demandant de confirmer que vous souhaitez renvoyer à ces abonnés.  

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
- Vous avez un grand nombre d’utilisateurs à ajouter ?  Découvrez comment attribuer des abonnements à [plusieurs abonnés](assign-license-bulk.md).
- Vous avez besoin d’aide ?  Contactez [Visual Studio Administration et Subscriptions Support](https://visualstudio.microsoft.com/support/support-overview-vs).


