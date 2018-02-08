---
Title: Assign licenses to Visual Studio Subscriptions | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can assign licenses to subscribers
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: b82f02b968398d0a8d1ce4872ce00e8447a2ae4d
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Attribution de licences dans le portail d’administration des abonnements Visual Studio

## <a name="assigning-a-single-user"></a>Attribution à un utilisateur unique
Si vous avez des licences disponibles pour les abonnements Visual Studio, vous pouvez les attribuer à de nouveaux utilisateurs pour leur donner accès aux avantages inclus dans leur abonnement. 
1.  Pour attribuer une licence à un seul abonné Visual Studio, cliquez sur **Ajouter** en haut du tableau.

    ![Ajouter un abonné](_img\assign-license-add\assign-license-add.png)

2.  Dans les champs de formulaire, entrez les informations relatives au nouvel abonné. Si votre organisation utilise Azure Active Directory, vous pouvez utiliser ce champ pour rechercher des utilisateurs dans votre annuaire actuel et sélectionner l’utilisateur approprié dans les résultats de la recherche. Une fois que vous avez sélectionné cet utilisateur, son nom, son adresse e-mail de connexion et son adresse e-mail de notification sont automatiquement renseignés, comme dans l’illustration ci-dessous. 

Si votre organisation utilise une adresse e-mail pour la réception des e-mails différente de l’adresse e-mail de connexion, vous pouvez l’entrer ici. Sélectionnez le lien hypertexte vous demandant si vos e-mails de notification et de connexion sont différents. 

Si vous souhaitez autoriser cet abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https:/my.visualstudio.com?wt.mc_id=o~msft~docs), laissez la case Téléchargements cochée. Si vous décochez cette case, l’utilisateur n’a pas accès aux téléchargements de logiciels, mais il garde l’accès à tous les autres avantages inclus dans son abonnement. Quand vous avez terminé, cliquez sur **Ajouter**.

   ![Entrez les informations de l’abonné](_img\assign-license-add\add-subscriber-1.png)

   ![Entrez les informations de l’abonné](_img\assign-license-add\add-subscriber-2.png)

3.  Après l’ajout de l’abonné, un e-mail d’attribution, contenant des instructions supplémentaires, est automatiquement envoyé au nouvel abonné. Vous pouvez renvoyer l’e-mail d’attribution à tout moment en sélectionnant l’abonné et en cliquant sur le bouton **Renvoyer** dans le menu supérieur.

    ![Abonné ajouté](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Attributions en bloc
1.  Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet Abonnés. Dans le ruban du haut, cliquez sur **Ajouter en bloc**. 

    ![Ajouter en bloc](_img\assign-license-add\bulk-assign-add.png)

2. L’attribution en bloc utilise un modèle Microsoft Excel pour charger les abonnés. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle. Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

    ![Charger plusieurs abonnés](_img\assign-license-add\bulk-assign-upload.png)

3.  Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. Le champ Référence est facultatif. Si vous avez mal renseigné un champ du modèle, un message d’erreur s’affiche pour signaler le problème. Enregistrez le fichier sur votre disque dur quand vous avez terminé.
**Pour faciliter le chargement, respectez les bonnes pratiques suivantes :**
    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après dans les champs de formulaire tels que les noms d’utilisateur.
    - Assurez-vous que les prénoms ou noms d’utilisateur en deux parties ne contiennent pas d’espace supplémentaire (par exemple, le prénom « Maggie May » ne doit pas être entré sous la forme « Maggie  May », car le système ne supprime pas l’espace supplémentaire).

   ![Modèle d’ajout en bloc](_img\assign-license-add\bulk-template.png)

4.  Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Parcourir**. Accédez au fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran. 

    ![Chargement de l’ajout en bloc](_img\assign-license-add\bulk-assign-upload-2.png)

Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.

   ![Échec du chargement](_img\assign-license-add\bulk-assign-upload-fail.png)

Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.

   ![Chargement terminé](_img\assign-license-add\bulk-assign-upload-complete.png)