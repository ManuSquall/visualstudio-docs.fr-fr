---
title: Supprimer des attributions d’abonnements dans le portail d’administration des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent supprimer des attributions d’abonnement
ms.openlocfilehash: 6ed64f5c05f77bea7f157eee9e29bbb05aa8730d
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263242"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Supprimer des attributions dans les abonnements Visual Studio
Quand un abonné n’a plus besoin d’un abonnement Visual Studio, par exemple quand il quitte l’entreprise, termine un projet ou change de fonction, vous pouvez supprimer son abonnement et l’attribuer à une autre personne. Notez que lorsque vous réattribuez un abonnement, tous les avantages de l’abonné ne sont pas réinitialisés.  Le nouvel utilisateur peut demander les clés non demandées et afficher celles précédemment demandées, mais le nombre maximal de demandes autorisées n’est **pas** réinitialisé.  Pour les organisations qui ont des contrats Entreprise, les avantages qui ont été utilisés par l’utilisateur initial, comme une formation Pluralsight, seront réinitialisés. 

## <a name="delete-a-subscription-assignment"></a>Supprimer une affectation d’abonnement
1. Cliquez sur le nom de l’abonné que vous voulez supprimer. Pour sélectionner plusieurs abonnés à supprimer, vous pouvez cliquer sur le cercle à gauche du nom de l’abonné pour en sélectionner un.  Vous pouvez également maintenir la touche **CTRL** enfoncée et cliquer sur chaque abonné que vous souhaitez supprimer.  Appuyez sur **Ctrl + A** pour sélectionner et supprimer tous les abonnés. 
2. Pour supprimer le ou les abonnés sélectionnés, cliquez sur **Supprimer**.
3. Quand le message de confirmation de la suppression s’affiche, cliquez sur **OK**.
   > [!div class="mx-imgBorder"]
   > ![Supprimer des abonnés](_img/delete-license/delete-subscribers.png)

   > [!NOTE]
   > La suppression en bloc à l’aide d’un modèle n’est pas disponible. Pour les organisations qui gèrent des affectations d’abonnements via des groupes de sécurité Azure Active Directory, consultez [notre article](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) pour plus d’informations sur la façon dont les suppressions se produisent.  

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous avez besoin de modifier un abonnement sans le supprimer ?  Découvrez comment [modifier des abonnements](edit-license.md)
- Pour obtenir de l’aide pour trouver un abonnement particulier, consultez [Rechercher un abonnement](search-license.md).
- Vous devez créer une liste de tous vos abonnements ?  Consultez [Exporter des abonnements](exporting-subscriptions.md).


