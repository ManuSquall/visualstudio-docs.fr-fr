---
title: Affecter des abonnements Visual Studio avec GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Gestion des abonnements dans les abonnements Visual Studio avec GitHub Enterprise
ms.openlocfilehash: c174b9beb7a7a0eec6bdb65e684869bc0be7dadb
ms.sourcegitcommit: 8da735b586276c95bf566a867655e3464ab1f989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109740662"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Gérer des abonnements Visual Studio avec GitHub Enterprise
Les clients qui ont des contrats entreprise avec Microsoft peuvent acheter une nouvelle offre d’abonnement qui regroupe des abonnements Visual Studio standard et GitHub Enterprise. Il s’agit d’un moyen simple et économique pour les abonnés Visual Studio d’acquérir GitHub Enterprise. 

Lorsque votre organisation achète des abonnements Visual Studio avec GitHub Enterprise, elle est approvisionnée et gérée en deux parties.

## <a name="manage-visual-studio-subscriptions"></a>Gérer les abonnements Visual Studio
Lorsque votre organisation achète des abonnements Visual Studio avec GitHub Enterprise, la partie Visual Studio des abonnements est approvisionnée immédiatement, et les abonnements sont disponibles pour l’attribution et la gestion dans le portail d' [administration des abonnements](https://manage.visualstudio.com) Visual Studio. Une fois que vous avez affecté un abonnement Visual Studio à GitHub Enterprise, l’abonné reçoit un message électronique lui indiquant qu’il peut accéder à son abonnement Visual Studio à l’adresse <https://my.visualstudio.com/subscriptions> .

Pour plus d’informations sur la gestion des abonnements Visual Studio, consultez les rubriques suivantes :
- [Utilisation du portail d’administration](using-admin-portal.md)
- [Affecter des abonnements](assign-license.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Surutilisations](handle-overclaimed-license.md)

> [!Important]
> Si les abonnements Visual Studio avec GitHub Enterprise sont affectés par les administrateurs des abonnements Visual Studio sans achat préalable, GitHub ne sera pas informé que vous souhaitez créer un compte GitHub Enterprise.  **Un achat d’au moins un** Un abonnement Visual Studio avec GitHub Enterprise doit être effectué avant l’attribution des abonnements.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Passage à Visual Studio avec GitHub Enterprise
Si votre organisation achète des abonnements Visual Studio avec des offres GitHub Enterprise après avoir attribué des abonnements à des Visual Studio Enterprise et des Visual Studio Professional standard, le portail d’administration contient une fonctionnalité qui vous permet de déplacer vos abonnés existants vers le Visual Studio Enterprise correspondant avec GitHub Enterprise et/ou Visual Studio Professional avec les abonnements GitHub Enterprise.  Par exemple, les abonnés avec des abonnements Visual Studio Professional seront déplacés vers Visual Studio Professional avec des abonnements GitHub Enterprise. Dans le panneau « vue d’ensemble » de la barre de gauche, vous verrez la vignette suivante :

   > [!div class="mx-imgBorder"]
   > ![Bouton déplacer maintenant](_img/assign-github/move-now.png "Cliquez sur « Déplacer maintenant » pour mettre à niveau les abonnements vers Visual Studio avec les abonnements GitHub Enterprise")

> [!IMPORTANT]
> Comme indiqué ci-dessus, les données, l’historique et l’ID d’abonnement de l’abonné existant sont conservés et les avantages qu’ils ont activés ne sont pas interrompus en raison de ce déplacement.  


Quand vous cliquez sur le bouton **Move Now (déplacer maintenant** ), un panneau volant vous présente des recommandations sur le déplacement de vos abonnements entreprise et/ou professionnel :

   > [!div class="mx-imgBorder"]
   > ![Panneau volant](_img/assign-github/fly-out.png)

Dans cette vignette, vous pouvez passer en revue les abonnés concernés et spécifier si vous souhaitez les notifier pour recevoir une notification par courrier électronique une fois le déplacement terminé.  Cet e-mail informe les abonnés que leurs avantages restent inchangés et les encourage à commencer à configurer une présence dans GitHub.  

En cliquant sur le bouton **déplacer**   les abonnés, vous pouvez déplacer tous les abonnés recommandés ou choisir des personnes dans une liste.  Une fois que vous avez confirmé vos sélections, le déplacement de l’abonnement peut prendre quelques secondes. Le cas échéant, vous devrez effectuer ces étapes séparément pour les éditions Professional et Enterprise.  

## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Qu’est-ce que le processus de configuration Visual Studio avec GitHub Enterprise ?
GitHub Enterprise est configuré et géré séparément des abonnements Visual Studio. À la suite d’un abonnement Visual Studio avec GitHub Enterprise Purchase, un processus de configuration d’un compte GitHub Enterprise est lancé en parallèle avec (mais distinct de) établissant un accord dans [Manage.VisualStudio.com](https://manage.visualstudio.com). La création de ce compte GitHub Enterprise peut prendre un certain temps. 

Une fois que votre société a configuré un compte GitHub Enterprise, les abonnés à qui ont été attribués des abonnements Visual Studio avec GitHub Enterprise reçoivent un e-mail de GitHub les notifiant que leurs abonnements Visual Studio ont été liés. Une fois que les abonnés reçoivent cet e-mail, ils peuvent contacter l’administrateur de leur organisation GitHub pour qu’ils reçoivent une invitation à l’organisation appropriée.

Pour plus d’informations sur l’installation de GitHub Enterprise, veuillez vous référer à la documentation de l' [abonné](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Gérer des abonnements GitHub Enterprise
Une fois les abonnements GitHub Enterprise achetés, GitHub partenaires avec les clients vous aide à créer et à configurer les organisations qui accéderont à GitHub et à identifier les administrateurs.  Ces administrateurs reçoivent ensuite une notification leur indiquant qu’ils ont été configurés en tant qu’administrateurs.  

Étant donné que ce processus est plus complexe, il peut falloir plusieurs jours après l’achat des abonnements pour que les organisations et les administrateurs soient entièrement configurés.

GitHub est disponible dans le cloud à l’adresse GitHub.com ou au niveau local par le biais de GitHub Enterprise Server.  Les processus de gestion des deux versions diffèrent.  GitHub fournit plusieurs rubriques d’aide et guides d’administration pour vous aider à gérer les abonnements GitHub Enterprise.  Vous trouverez ci-dessous des liens vers certaines rubriques.  

## <a name="support-resources"></a>Ressources de support
- En savoir plus sur l’affectation de GitHub dans [GitHub docs](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Trouvez des réponses aux questions sur une vaste gamme de rubriques GitHub dans [l’aide de GitHub](https://help.github.com/en).
- Vous pouvez également solliciter l’aide d’autres utilisateurs de GitHub dans le [forum de la communauté GitHub](https://github.community/).
- Pour obtenir de l’aide sur l’administration des abonnements Visual Studio, contactez le [support des abonnements Visual Studio](https://aka.ms/vsadminhelp).
- Vous avez des questions concernant l’IDE Visual Studio, Azure DevOps Services, ou d’autres produits ou services Visual Studio ?  Consultez le [support Visual Studio](https://visualstudio.microsoft.com/support/).
- Contactez le [support technique](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) de GitHub Enterprise.   

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)

Pour plus d’informations sur la gestion des abonnements Visual Studio avec GitHub Enterprise, consultez le [portail d’administration des abonnements](https://visualstudio.microsoft.com/subscriptions-administration/)Visual Studio.