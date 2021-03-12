---
title: Supprimer les affectations d’abonnements Visual Studio dans le portail d’administration des abonnements | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 02/18/2021
ms.topic: how-to
description: Découvrez comment les administrateurs peuvent supprimer des affectations d’abonnements dans le portail d’administration des abonnements Visual Studio
ms.openlocfilehash: efd0e149f390dd21a286b6ab7405ec36a43b8f78
ms.sourcegitcommit: 9da787bf5b4281f933dc22083dc0bdeae3bc9461
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103225974"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Supprimer des attributions dans les abonnements Visual Studio
Quand un abonné n’a plus besoin d’un abonnement Visual Studio, par exemple quand il sort de l’entreprise, termine un projet ou bascule vers un nouveau rôle, vous pouvez supprimer son abonnement et l’attribuer à une autre personne. Notez que lorsque vous réattribuez un abonnement, tous les avantages de l’abonné ne sont pas réinitialisés.  Le nouvel utilisateur peut demander les clés non demandées et afficher celles précédemment demandées, mais le nombre maximal de demandes autorisées n’est **pas** réinitialisé.  Pour les organisations qui ont des contrats Entreprise, les avantages qui ont été utilisés par l’utilisateur initial, comme une formation Pluralsight, seront réinitialisés. 
> [!Important]
> Les abonnements ne peuvent être attribués qu’à des utilisateurs distincts si un minimum de 90 jours se sont écoulés depuis la dernière attribution de l’abonnement.  Par exemple, si un abonnement a été attribué à un abonné le 1er juin, il ne peut pas être attribué à un nouvel abonné jusqu’au 30 août. 

Regardez cette vidéo ou lisez la suite pour apprendre à supprimer des affectations.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Supprimer une affectation d’abonnement
1. Cliquez sur le nom de l’abonné que vous voulez supprimer. Pour sélectionner plusieurs abonnés à supprimer, vous pouvez cliquer sur le cercle à gauche du nom de l’abonné pour en sélectionner un.  Vous pouvez également maintenir la touche **CTRL** enfoncée et cliquer sur chaque abonné que vous souhaitez supprimer. Pour supprimer une plage d’abonnés, cliquez sur le premier, appuyez sur la touche **MAJ** , puis cliquez sur le dernier.  Appuyez sur **Ctrl + A** pour sélectionner et supprimer tous les abonnés. Dans cet exemple, trois abonnés-ambre, Kai et Madison-seront supprimés. 
2. Pour supprimer le ou les abonnés sélectionnés, cliquez sur **Supprimer**.
3. Quand le message de confirmation de la suppression s’affiche, cliquez sur **OK**.
   > [!div class="mx-imgBorder"]
   > ![Supprimer des abonnés](_img/delete-license/delete-subscribers.png "Choisissez le ou les utilisateurs que vous souhaitez supprimer, puis cliquez sur supprimer. Vous pouvez utiliser les touches CTRL et Maj pour sélectionner plusieurs abonnés.")

   > [!NOTE]
   > La suppression en bloc à l’aide d’un modèle n’est pas disponible. 
   >
   > Si vous avez ajouté des affectations d’abonnement par le biais de Azure Active Directory groupes de sécurité, la suppression de la suppression dans le portail d’administration peut prendre jusqu’à 24 heures.  Pour plus d’informations sur l’utilisation des groupes de Azure Active Directory pour gérer les abonnements, consultez [notre article](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) . 

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous avez besoin de modifier un abonnement sans le supprimer ?  Découvrez comment [modifier des abonnements](edit-license.md)
- Pour obtenir de l’aide pour trouver un abonnement particulier, consultez [Rechercher un abonnement](search-license.md).
- Vous devez créer une liste de tous vos abonnements ?  Consultez [Exporter des abonnements](exporting-subscriptions.md).