---
title: Rôles Super administrateur et Administrateur dans le portail d’administration
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Découvrez les rôles Super administrateur et Administrateur, et comment affecter des administrateurs.
ms.openlocfilehash: ef0ba479c099bf1e34fe871386984297b130ffd6
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78234821"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super administrateurs et administrateurs pour les contrats d’abonnement Visual Studio

Il existe deux rôles différents dans le nouveau portail d’administration des abonnements Visual Studio pour les clients avec licence en volume. Ces rôles sont similaires au rôle Contact principal/Destinataire des avis et Gestionnaire d’abonnements qui existaient dans le Centre de gestion des licences en volume (VLSC).

**Super admins:** Lorsqu’une organisation est initialement créée, le Contact Primaire ou Avis devient un super admin par défaut. Le contact principal ou l’interlocuteur pour les notifications peut choisir d’affecter des super administrateurs ou des administrateurs supplémentaires. Un super administrateur peut ajouter et supprimer d’autres administrateurs, ainsi que des abonnés. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en garder au minimum deux pour des raisons de sécurité.

**Administrateurs:** Un administrateur ne peut être assigné que par un super administrateur. Un administrateur ne peut gérer les abonnés que dans les accords que le super administrateur leur assigne.

## <a name="assigning-administrators"></a>Affectation des administrateurs
Pour affecter de nouveaux administrateurs :
1. Connectez-vous à https://manage.visualstudio.com en utilisant une adresse e-mail qui est affectée en tant que super administrateur au contrat par le biais duquel les abonnements ont été achetés.
2. Cliquez sur l’onglet libellé **Gérer les administrateurs**.
3. Cliquez sur **Ajouter**.
   > [!div class="mx-imgBorder"]
   > ![Ajouter des administrateurs](_img/admin-roles/add-admins.png)
4. Complétez le formulaire avec les informations du nouvel administrateur.  
   > [!div class="mx-imgBorder"]
   > ![Formulaire Ajouter un administrateur](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Si vous voulez que cet administrateur puisse affecter des administrateurs supplémentaires, n’oubliez pas de cocher la case **Super administrateur**.

5. Une fois que vous avez cliqué sur **Ajouter** pour affecter le nouvel administrateur, celui-ci reçoit un e-mail l’invitant à se connecter au portail.  

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements et de l’administration Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
- Découvrir comment [attribuer des abonnements](assign-license.md)
- Découvrir plus d’informations sur la gamme complète des [avantages des abonnements](https://visualstudio.microsoft.com/vs/benefits/)
- [Définir les préférences de contrat](admin-prefs.md) 


