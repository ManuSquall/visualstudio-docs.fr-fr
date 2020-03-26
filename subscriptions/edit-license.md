---
title: Modifier les abonnements dans le portail d’administration | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent modifier des attributions d’abonnement.
ms.openlocfilehash: d145d556467b4eecec787fe409b4faa45945bec0
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232551"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Modifier des attributions d’abonnements Visual Studio
En tant qu’administrateur des abonnements, vous pouvez apporter des modifications aux abonnements attribués à des personnes au sein de votre organisation.  Cet article décrit les types de modifications que vous pouvez apporter et indique les étapes à suivre.

   > [!NOTE]
   > Si vous avez besoin de modifier les détails d’abonnement d’un abonné assigné par l’intermédiaire d’un groupe d’annuaires Azure Active, vous devrez les supprimer du groupe et les ajouter individuellement au Portail d’Administration.  

## <a name="change-subscriber-information"></a>Changer les informations de l’abonné
Vous pouvez modifier les informations d’un abonné pour corriger des erreurs ou mettre à jour les informations le concernant.

Pour modifier les informations d’un abonné, sélectionnez les points de suspension (...) à côté de l’adresse e-mail de l’abonné en pointant dessus. Une liste déroulante s’affiche.  Sélectionnez **Modifier** pour modifier les informations de l’abonné. 
> [!div class="mx-imgBorder"]
> ![Sélectionner l’abonné à modifier](_img/edit-license/select-subscriber.png)

Vous pouvez mettre à jour le prénom, le nom de famille, le niveau d’abonnement, l’adresse e-mail, le pays, la langue, les téléchargements et le champ de référence de l’abonné. Modifier les informations de l’abonné, et cliquez sur **Enregistrer**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Modifier plusieurs abonnés à l’aide de la modification en bloc
Vous pouvez modifier plusieurs abonnés à la fois en effectuant une modification en bloc. Cette fonctionnalité est principalement destinée aux organisations qui doivent changer les adresses e-mail de façon globale ou aux organisations qui souhaitent restreindre l’accès aux téléchargements.

   > [!IMPORTANT]
   > Les niveaux d’abonnement (c.-à-d. guiDs d’entreprise, professionnels, etc.) et d’abonnement ne peuvent pas être modifiés à l’aide de l’édition en vrac.  Si vous avez besoin d’attribuer des GUIDs d’abonnement spécifiques à vous les utilisateurs, utilisez le processus d’ajout d’utilisateurs en choisissant l’ID d’abonnement. Si vous tentez un téléchargement avec ces éléments modifiés dans le modèle de modification en vrac, le téléchargement échouera.

1. Pour modifier plusieurs abonnés à la fois, accédez à l’onglet Abonnés. Dans le ruban en haut, cliquez sur **Bulk Edit**.

2. La modification en bloc utilise un modèle Excel pour apporter des modifications aux informations des abonnés. Dans la zone Modifier en bloc, cliquez sur **Exporter cette feuille Excel** pour télécharger la liste actuelle des abonnés et toutes les informations associées.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Exporter la liste des modifications en bloc](_img/edit-license/edit-license-bulk-edit-export.png)

3. Ensuite, enregistrez le fichier à un emplacement local pour pouvoir le retrouver facilement si vous avez besoin d’y apporter des modifications avant le chargement. Pour assurer un téléchargement réussi, **ne modifiez pas le niveau d’abonnement ou l’abonnement GUID** dans le fichier de modification en vrac, ce qui entraînera l’échec du téléchargement.

4. Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue Modification en bloc, cliquez sur **Parcourir**. Sélectionnez le fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Chargement du fichier des modifications en bloc](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Une fois que vous avez chargé le fichier, vous voyez s’afficher une notification confirmant le chargement. À ce stade, vos modifications apparaissent dans les informations de l’abonné.

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Besoin d’attribuer un id d’abonnement spécifique? Consultez l’attribution d’un identifiant d’abonnement. 
- Pour obtenir de l’aide pour trouver un abonnement particulier, consultez [Rechercher un abonnement](search-license.md).
- Vous devez créer une liste de tous vos abonnements ?  Consultez [Exporter des abonnements](exporting-subscriptions.md).


