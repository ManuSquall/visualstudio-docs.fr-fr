---
title: Rôles Super administrateur et Administrateur dans le portail d’administration
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 09/21/2020
ms.topic: conceptual
description: Découvrez les rôles Super administrateur et Administrateur, et comment affecter des administrateurs.
ms.openlocfilehash: fc44845ed403e9bf942761203b75c2277fd1aff2
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "91022696"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super administrateurs et administrateurs pour les contrats d’abonnement Visual Studio

Il existe deux rôles différents dans le nouveau portail d’administration des abonnements Visual Studio pour les clients avec licence en volume. Ces rôles sont similaires au rôle Contact principal/Destinataire des avis et Gestionnaire d’abonnements qui existaient dans le Centre de gestion des licences en volume (VLSC).

**Super administrateurs :** Lors de la configuration initiale d’une organisation, le contact principal ou le contact avis devient un super administrateur par défaut. Le contact principal ou l’interlocuteur pour les notifications peut choisir d’affecter des super administrateurs ou des administrateurs supplémentaires. Un super administrateur peut ajouter et supprimer d’autres administrateurs, ainsi que des abonnés. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en garder au minimum deux pour des raisons de sécurité.

**Administrateurs :** Un administrateur ne peut être attribué qu’à un super administrateur. Un administrateur peut uniquement gérer les abonnés dans les contrats que le Super administrateur leur affecte.

Regardez une démonstration sur la gestion des administrateurs. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Affectation des administrateurs
Pour affecter de nouveaux administrateurs :
1. Connectez-vous à https://manage.visualstudio.com en utilisant une adresse e-mail qui est affectée en tant que super administrateur au contrat par le biais duquel les abonnements ont été achetés.
2. Cliquez sur l’onglet libellé **Gérer les administrateurs**.
3. Cliquez sur **Add**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter des administrateurs](_img/admin-roles/add-admins.png "Cliquez sur le panneau gérer les administrateurs, puis sur Ajouter pour affecter de nouveaux administrateurs.")
4. Complétez le formulaire avec les informations du nouvel administrateur.  
   > [!div class="mx-imgBorder"]
   > ![Formulaire Ajouter un administrateur](_img/admin-roles/add-form.png "Entrez les informations de connexion du nouvel administrateur et indiquez si vous souhaitez en faire un super administrateur.  Cliquez ensuite sur Ajouter.")

   > [!NOTE]
   > Si vous voulez que cet administrateur puisse affecter des administrateurs supplémentaires, n’oubliez pas de cocher la case **Super administrateur**.

5. Une fois que vous avez cliqué sur **Ajouter** pour affecter le nouvel administrateur, celui-ci reçoit un e-mail l’invitant à se connecter au portail.  

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements et de l’administration de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
- Découvrir comment [attribuer des abonnements](assign-license.md)
- Découvrir plus d’informations sur la gamme complète des [avantages des abonnements](https://visualstudio.microsoft.com/vs/benefits/)
- [Définir les préférences de contrat](admin-prefs.md)