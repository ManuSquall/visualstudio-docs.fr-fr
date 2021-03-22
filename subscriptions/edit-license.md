---
title: Modifier des abonnements Visual Studio dans le portail d’administration | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/21/2021
ms.topic: how-to
description: Découvrez comment les administrateurs peuvent modifier les affectations d’abonnements.
ms.openlocfilehash: b1779b80cc295e680ff1856181be42a6390fe25b
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776868"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Modifier des attributions d’abonnements Visual Studio
En tant qu’administrateur d’abonnements, vous pouvez apporter des modifications aux abonnements attribués à des personnes au sein de votre organisation.  Cet article décrit les types de modifications que vous pouvez apporter et indique les étapes à suivre.

   > [!NOTE]
   > Si vous devez modifier les informations d’abonnement d’un abonné affecté via un groupe de Azure Active Directory, vous devez les supprimer du groupe et les ajouter au portail d’administration individuellement.  

## <a name="change-subscriber-information"></a>Changer les informations de l’abonné
Vous pouvez modifier les informations d’un abonné pour corriger des erreurs ou mettre à jour les informations le concernant.

Pour modifier les informations d’un abonné, sélectionnez les points de suspension (...) à côté de l’adresse e-mail de l’abonné en pointant dessus. Une liste déroulante s’affiche.  Sélectionnez **Modifier** pour modifier les informations de l’abonné. 
> [!div class="mx-imgBorder"]
> ![Sélectionner l’abonné à modifier](_img/edit-license/select-subscriber.png "Cliquez sur les ellipses, puis choisissez Modifier.")

Vous pouvez mettre à jour le prénom, le nom, le niveau d’abonnement, l’adresse de messagerie, le pays, la langue, les téléchargements et le champ de référence de l’abonné. Modifiez les informations de l’abonné, puis cliquez sur **Enregistrer**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Modifier plusieurs abonnés à l’aide de la modification en bloc

Vous pouvez modifier plusieurs abonnés à la fois en effectuant une modification en bloc. Cette fonctionnalité est principalement destinée aux organisations qui doivent changer les adresses e-mail de façon globale ou aux organisations qui souhaitent restreindre l’accès aux téléchargements.

Regardez cette vidéo ou lisez pour savoir comment modifier plusieurs abonnés à l’aide de la modification en bloc. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> Ne modifiez pas les GUID d’abonnement dans le modèle. Pour plus d’informations sur l' [affectation de GUID d’abonnement spécifiques](assign-guid.md), consultez notre article.

1. Pour modifier plusieurs abonnés à la fois, accédez à l’onglet abonnés. Dans le ruban en haut, cliquez sur **modification en bloc**.

2. La modification en bloc utilise un modèle Excel pour apporter des modifications aux informations des abonnés. Dans la zone Modifier en bloc, cliquez sur **Exporter cette feuille Excel** pour télécharger la liste actuelle des abonnés et toutes les informations associées.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Exporter la liste des modifications en bloc](_img/edit-license/edit-license-bulk-edit-export.png "Cliquez sur exporter ce Excel pour créer une liste de vos abonnements actuels.")

3. Ensuite, enregistrez le fichier à un emplacement local pour pouvoir le retrouver facilement si vous avez besoin d’y apporter des modifications avant le chargement. 

4. Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue Modification en bloc, cliquez sur **Parcourir**. Sélectionnez le fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Chargement du fichier des modifications en bloc](_img/edit-license/edit-license-bulk-file-upload1.png "Accédez à l’emplacement de votre fichier Excel terminé, sélectionnez-le, puis cliquez sur OK.")

5. Une fois que vous avez chargé le fichier, vous voyez s’afficher une notification confirmant le chargement. À ce stade, vos modifications apparaissent dans les informations de l’abonné.

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous devez affecter un ID d’abonnement spécifique ? Consultez attribution d’un ID d’abonnement. 
- Pour obtenir de l’aide pour trouver un abonnement particulier, consultez [Rechercher un abonnement](search-license.md).
- Vous devez créer une liste de tous vos abonnements ?  Consultez [Exporter des abonnements](exporting-subscriptions.md).