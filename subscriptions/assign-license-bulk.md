---
title: Attribuer des licences à des groupes d’utilisateurs pour des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences à plusieurs abonnés
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610519"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Attribuer des abonnements à plusieurs utilisateurs
Le portail d’administration des abonnements vous permet d’ajouter des utilisateurs un à la fois ou dans des grands groupes.  Pour ajouter des utilisateurs individuels, consultez [Ajouter des utilisateurs uniques](assign-license.md).

## <a name="use-bulk-add-to-assign-subscriptions"></a>Utiliser l’ajout en bloc pour attribuer des abonnements
1. Connectez-vous au portail d’administration des abonnements Visual Studio à l’adresse https://manage.visualstudio.com.
2. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **Gérer les abonnés**. Dans le ruban du haut, cliquez sur **Ajouter en bloc**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter plusieurs abonnés](media/add-multiple-subscribers.png)

2. La fonctionnalité Ajouter en bloc utilise un modèle Microsoft Excel pour charger les informations des abonnés. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle.
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

## <a name="next-steps"></a>Étapes suivantes
- Vous n’avez qu’un ou deux abonnés à ajouter ?  Consultez [Ajouter des utilisateurs uniques](assign-license.md)
- Découvrez comment [modifier](edit-license.md) des abonnements existants
- Vous avez besoin d'aide ? Contactez le [Support technique sur l’administration et les abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
