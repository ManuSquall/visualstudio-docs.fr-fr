---
title: Modifier les abonnements dans le portail d’administration | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Découvrez comment les administrateurs peuvent modifier des attributions d’abonnement.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4ee209af97d09f5d7e2125d2111746f6fe491f5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34476636"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Modification des attributions d’abonnements Visual Studio

En tant qu’administrateur des abonnements, vous pouvez apporter des modifications aux abonnements attribués à des personnes au sein de votre organisation.  Cet article décrit les types de modifications que vous pouvez apporter et indique les étapes à suivre. 

## <a name="making-changes-to-subscriber-information"></a>Modifier les informations d’un abonné
Vous pouvez modifier les informations d’un abonné pour corriger des erreurs ou mettre à jour les informations le concernant. 

Pour modifier les informations d’un abonné, sélectionnez les points de suspension (...) à côté de l’adresse e-mail de l’abonné en pointant dessus. Une liste déroulante s’affiche.  Sélectionnez **Modifier** pour modifier les informations de l’abonné. Vous pouvez également double-cliquer sur la ligne de l’abonné dans la grille pour ouvrir la fenêtre d’édition.

   <img alt="Select subscriber to edit" src="_img\edit-license\select-subscriber.png" style="border: 1px solid #CCCCCC" />
    
Vous pouvez mettre à jour le prénom, le nom, le pays, la langue et les téléchargements de l’abonné. Modifiez les informations de l’abonné, puis cliquez sur **Enregistrer**.

 
   <img alt="Edit subscriber details" src="_img\edit-license\edit-subscriber.png" style="border: 1px solid #CCCCCC" />
   > [!NOTE]
   > Pour changer le niveau d’abonnement d’un abonné, vous devez supprimer l’utilisateur du portail, puis l’ajouter de nouveau. Les niveaux d’abonnement ne sont pas modifiables directement.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Modification de plusieurs abonnés à l’aide de la modification en bloc

Vous pouvez modifier plusieurs abonnés à la fois en effectuant une modification en bloc. Cette fonctionnalité est principalement destinée aux organisations qui doivent changer les adresses e-mail de façon globale ou aux organisations qui souhaitent restreindre l’accès aux téléchargements. 

   > [!IMPORTANT]
   > Les niveaux d’abonnement (Enterprise, Professional, etc.) et les GUID d’abonnement ne doivent pas être modifiés.  Si vous essayez d’effectuer un chargement après avoir modifié ces éléments, le chargement échoue.  

1.  Pour modifier plusieurs abonnés à la fois, accédez à l’onglet Abonnés. Dans le ruban du haut, cliquez sur **Modifier en bloc**. 

    <img alt="Editing a License - Bulk Edits" src="_img\edit-license\edit-license-bulk-edit.png" style="border: 1px solid #CCCCCC" />

2.  La modification en bloc utilise un modèle Excel pour apporter des modifications aux informations des abonnés. Dans la zone Modifier en bloc, cliquez sur **Exporter cette feuille Excel** pour télécharger la liste actuelle des abonnés et toutes les informations associées. 

    <img alt="Editing a License - Export Bulk Edits List" src="_img\edit-license\edit-license-bulk-edit-export.png" style="border: 1px solid #CCCCCC" />

3.  Ensuite, enregistrez le fichier à un emplacement local pour pouvoir le retrouver facilement si vous avez besoin d’y apporter des modifications avant le chargement. Pour garantir la réussite du chargement, **ne modifiez pas le niveau ni le GUID de l’abonnement**, car cela entraîne l’échec du chargement. 

4.  Revenez au portail d’administration des abonnements Visual Studio et, dans la boîte de dialogue Modification en bloc, cliquez sur **Parcourir**. Sélectionnez le fichier Excel que vous avez enregistré, puis cliquez sur **OK**. Vous pouvez observer la progression du chargement à l’écran.

    <img alt="Editing a License - Bulk Edits File Upload" src="_img\edit-license\edit-license-bulk-file-upload1.png" style="border: 1px solid #CCCCCC" />

5.  Une fois que vous avez chargé le fichier, vous voyez s’afficher une notification confirmant le chargement. À ce stade, vos modifications apparaissent dans les informations de l’abonné. 

    <img alt="Editing a License - Bulk Edits Upload Complete" src="_img\edit-license\edit-license-bulk-upload-complete.png" style="border: 1px solid #CCCCCC" />

