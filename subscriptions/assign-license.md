---
title: Attribuer des licences à des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Découvrez comment les administrateurs peuvent attribuer des licences aux abonnés
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4325921bbaa75e0fb8a8a16947c45901b6f01649
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477377"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Attribution de licences dans le portail d’administration des abonnements Visual Studio

En tant qu’administrateur des abonnements Visual Studio, vous pouvez utiliser le portail d’administration des abonnements Visual Studio pour attribuer individuellement des abonnements à des utilisateurs.  
Vous pouvez les attribuer individuellement un à la fois ou utiliser la fonctionnalité « Ajouter en bloc » pour charger rapidement et facilement des listes d’abonnés avec leurs informations d’abonnement. 

## <a name="assigning-a-single-user"></a>Attribution à un utilisateur unique
Si vous avez des licences disponibles pour les abonnements Visual Studio, vous pouvez les attribuer à de nouveaux utilisateurs pour leur donner accès aux avantages inclus dans leur abonnement. 
1.  Connectez-vous au [portail d’administration](https://manage.visualstudio.com)

2.  Pour attribuer une licence à un seul abonné Visual Studio, cliquez sur **Ajouter** en haut du tableau.

    <img alt="Add subscriber" src="_img\assign-license-add\assign-license-add.png" style="border: 1px solid #CCCCCC" />

3.  Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, vous pouvez utiliser ce champ pour rechercher des utilisateurs dans votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cet utilisateur, son nom, son adresse e-mail de connexion et son adresse e-mail de notification sont automatiquement renseignés, comme dans l’illustration ci-dessous. 

    Si votre organisation n’utilise pas Azure Active Directory (Azure AD) mais utilise une adresse e-mail pour la réception des e-mails différente de l’adresse e-mail de connexion, vous pouvez l’entrer ici. Sélectionnez le lien hypertexte nommé « Ajouter un autre e-mail pour la réception des communications ». 

    **Accéder aux téléchargements :**  
    Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements activée. Si vous choisissez de désactiver les téléchargements, l’utilisateur n’a pas accès aux téléchargements de logiciels, mais il garde l’accès à tous les autres avantages inclus dans son abonnement. 
    
    Une fois que vous avez fini de choisir les options pour cet abonné, cliquez sur **Ajouter**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  Après l’ajout de l’abonné, un e-mail d’attribution, contenant des instructions supplémentaires, est automatiquement envoyé au nouvel abonné. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **Renvoyer** dans le menu supérieur.

    <img alt="Subscriber added" src="_img\assign-license-add\add-subscriber-complete.png" style="border: 1px solid #CCCCCC" />

## <a name="bulk-assignments"></a>Attributions en bloc
1.  Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **Gérer les abonnés**. Dans le ruban du haut, cliquez sur **Ajouter en bloc**. 

    <img alt="Bulk add" src="_img\assign-license-add\bulk-assign-add.png" style="border: 1px solid #CCCCCC" />

2. L’attribution en bloc utilise un modèle Microsoft Excel pour charger les abonnés. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle. Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

    <img alt="Upload multiple subscribers" src="_img\assign-license-add\bulk-assign-upload.png" style="border: 1px solid #CCCCCC" />

3.  Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. Le champ Référence est facultatif. Si vous avez mal renseigné un champ du modèle, un message d’erreur s’affiche pour signaler le problème. Enregistrez le fichier localement une fois terminé.
**Pour faciliter le chargement, respectez les bonnes pratiques suivantes :**
    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après dans les champs de formulaire tels que les noms d’utilisateur.
    - Assurez-vous que les prénoms ou noms d’utilisateur en deux parties ne contiennent pas d’espace supplémentaire (par exemple, le prénom « Maggie May » ne doit pas être entré sous la forme « Maggie  May », car le système ne supprime pas l’espace supplémentaire).
    <img alt="Bulk add template" src="_img\assign-license-add\bulk-template.png" style="border: 1px solid #CCCCCC" />

4.  Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Parcourir**. Accédez au fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.

   <img alt="Upload complete" src="_img\assign-license-add\bulk-assign-upload-complete.png" style="border: 1px solid #CCCCCC" />