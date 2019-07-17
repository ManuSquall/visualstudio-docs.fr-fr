---
title: Modifier les abonnements dans le portail d’administration | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent modifier des attributions d’abonnement.
ms.openlocfilehash: 7245facbaf966593160bc44dc15bc2fd71622347
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783474"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Modification des attributions d’abonnements Visual Studio

En tant qu’administrateur des abonnements, vous pouvez apporter des modifications aux abonnements attribués à des personnes au sein de votre organisation.  Cet article décrit les types de modifications que vous pouvez apporter et indique les étapes à suivre.

## <a name="making-changes-to-subscriber-information"></a>Modifier les informations d’un abonné
Vous pouvez modifier les informations d’un abonné pour corriger des erreurs ou mettre à jour les informations le concernant.

Pour modifier les informations d’un abonné, sélectionnez les points de suspension (...) à côté de l’adresse e-mail de l’abonné en pointant dessus. Une liste déroulante s’affiche.  Sélectionnez **Modifier** pour modifier les informations de l’abonné. Vous pouvez également double-cliquer sur la ligne de l’abonné dans la grille pour ouvrir la fenêtre d’édition.
> [!div class="mx-imgBorder"]
> ![Sélectionner l’abonné à modifier](_img/edit-license/select-subscriber.png)

Vous pouvez mettre à jour le prénom, le nom, le pays, la langue et les téléchargements de l’abonné. Modifiez les informations de l’abonné, puis cliquez sur **Enregistrer**.

   > [!NOTE]
   > Pour changer le niveau d’abonnement d’un abonné, vous devez supprimer l’utilisateur du portail, puis l’ajouter de nouveau. Les niveaux d’abonnement ne sont pas modifiables directement.

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>Modification de plusieurs abonnés à l’aide de la modification en bloc

Vous pouvez modifier plusieurs abonnés à la fois en effectuant une modification en bloc. Cette fonctionnalité est principalement destinée aux organisations qui doivent changer les adresses e-mail de façon globale ou aux organisations qui souhaitent restreindre l’accès aux téléchargements.

   > [!IMPORTANT]
   > Les niveaux d’abonnement (Enterprise, Professional, etc.) et les GUID d’abonnement ne doivent pas être modifiés.  Si vous essayez d’effectuer un chargement après avoir modifié ces éléments, le chargement échoue.

1. Pour modifier plusieurs abonnés à la fois, accédez à l’onglet Abonnés. Dans le ruban du haut, cliquez sur **Modifier en bloc**.

2. La modification en bloc utilise un modèle Excel pour apporter des modifications aux informations des abonnés. Dans la zone Modifier en bloc, cliquez sur **Exporter cette feuille Excel** pour télécharger la liste actuelle des abonnés et toutes les informations associées.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Exporter la liste des modifications en bloc](_img/edit-license/edit-license-bulk-edit-export.png)

3. Ensuite, enregistrez le fichier à un emplacement local pour pouvoir le retrouver facilement si vous avez besoin d’y apporter des modifications avant le chargement. Pour garantir la réussite du chargement, **ne modifiez pas le niveau ni le GUID de l’abonnement**, car cela entraîne l’échec du chargement.

4. Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue Modification en bloc, cliquez sur **Parcourir**. Sélectionnez le fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran.
   > [!div class="mx-imgBorder"]
   > ![Modification d’une licence - Chargement du fichier des modifications en bloc](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Une fois que vous avez chargé le fichier, vous voyez s’afficher une notification confirmant le chargement. À ce stade, vos modifications apparaissent dans les informations de l’abonné.
