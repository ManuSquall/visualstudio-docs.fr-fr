---
title: "Modifier les abonnements dans le portail d’administration | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can edit subscription assignments.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c561e7a56f2e70cae1addd32902f68a582b49a02
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="editing-visual-studio-subscription-assignments"></a>Modification des attributions d’abonnement Visual Studio

## <a name="making-changes-to-subscriber-information"></a>Modifier les informations d’un abonné
Vous pouvez modifier les informations d’un abonné pour corriger des erreurs ou mettre à jour les informations le concernant. 
**Notez que le changement de l’adresse e-mail d’un abonné entraîne la réinitialisation de tous les avantages existants.**

Pour modifier les informations d’un abonné, sélectionnez les points de suspension (...) à côté de l’adresse e-mail de l’abonné en pointant dessus. Une liste déroulante s’affiche.  Sélectionnez **Modifier** pour modifier les informations de l’abonné. Vous pouvez également double-cliquer sur la ligne de l’abonné dans la grille pour ouvrir la fenêtre d’édition.

   ![Sélectionner l’abonné à modifier](_img\edit-license\select-subscriber.png)

Vous pouvez mettre à jour le prénom, le nom, le pays, la langue et les téléchargements de l’abonné. Modifiez les informations de l’abonné, puis cliquez sur **Enregistrer**.

   ![Modifier les informations de l’abonné](_img\edit-license\edit-subscriber.png)

Remarque : Pour changer le niveau d’abonnement d’un abonné, vous devez supprimer l’utilisateur à partir du portail et l’ajouter à nouveau. Les niveaux d’abonnement ne sont pas modifiables directement.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Modification de plusieurs abonnés à l’aide de la modification en bloc

Vous pouvez modifier plusieurs abonnés à la fois en effectuant une modification en bloc. Cette fonctionnalité est principalement destinée aux organisations qui doivent changer les adresses e-mail de façon globale ou aux organisations qui souhaitent restreindre l’accès aux téléchargements. 

**IMPORTANT** : Les niveaux d’abonnement (Enterprise, Professional, etc.) et les GUID d’abonnement ne doivent pas être modifiés.  Si vous essayez d’effectuer un chargement après avoir modifié ces éléments, le chargement échoue.  

1.  Pour modifier plusieurs abonnés à la fois, accédez à l’onglet Abonnés. Dans le ruban du haut, cliquez sur **Modifier en bloc**. 

    ![Modification d’une licence - Modifications en bloc](_img\edit-license\edit-license-bulk-edit.png)

2.  La modification en bloc utilise un modèle Excel pour apporter des modifications aux informations des abonnés. Dans la zone Modifier en bloc, cliquez sur **Exporter cette feuille Excel** pour télécharger la liste actuelle des abonnés et toutes les informations associées. 

    ![Modification d’une licence - Exporter la liste des modifications en bloc](_img\edit-license\edit-license-bulk-edit-export.png)

3.  Ensuite, enregistrez le fichier à un emplacement local pour pouvoir le retrouver facilement si vous avez besoin d’y apporter des modifications avant le chargement. Pour garantir la réussite du chargement, **ne modifiez pas le niveau ni le GUID de l’abonnement**, car cela entraîne l’échec du chargement. 

4.  Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue Modification en bloc, cliquez sur **Parcourir**. Sélectionnez le fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran.

    ![Modification d’une licence - Chargement du fichier des modifications en bloc](_img\edit-license\edit-license-bulk-file-upload1.png)

5.  Une fois que vous avez chargé le fichier, vous voyez s’afficher une notification confirmant le chargement. 

    ![Modification d’une licence - Chargement des modifications en bloc terminé](_img\edit-license\edit-license-bulk-upload-complete.png)


