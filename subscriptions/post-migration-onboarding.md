---
title: Effectuer l’intégration au portail d’administration des abonnements Visual Studio après la migration
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 07/12/2018
ms.topic: conceptual
description: Découvrez comment intégrer correctement votre organisation aux abonnements Visual Studio après la migration vers le portail d’administration.
searchscope: VS Subscription
ms.openlocfilehash: 3916fd762e9a2feaaa4892e4233d08a345db44a1
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954226"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-is-migrated"></a>Effectuer l’intégration au portail d’administration des abonnements Visual Studio après la migration de votre organisation

Si vous avez géré les abonnements Visual Studio dans le centre de gestion des licences en volume (VLSC) Microsoft et que vous avez récemment visité le site pour gérer des abonnements, vous remarquerez que la gestion des abonnements n’est plus disponible dans le VLSC. Votre processus de gestion des abonnements devait ressembler à ça :
> [!div class="mx-imgBorder"]
> ![Capture d’écran du VLSC Microsoft, avec l’onglet Abonnements mis en surbrillance](_img/post-migration-onboarding/vlsc-subscriptions.png)

Toutefois, les abonnements sont désormais gérés via un nouveau portail appelé portail d’administration abonnements Visual Studio. En général, le contact principal ou le destinataire des notifications pour le contrat de licence en volume de votre organisation effectue cette procédure. Si ce n’est pas le cas, les informations suivantes vous permettent d’accéder à la gestion des abonnements.

Vous pouvez rencontrer un des cas suivants :

1. [Le contact principal n’a pas terminé le processus d’intégration.](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2. [Le contact principal a effectué l’intégration, mais ne vous a pas ajouté en tant qu’administrateur. Vos informations d’identification ont été répertoriées dans VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3. [Le contact principal a effectué l’intégration, mais ne vous a pas ajouté en tant qu’administrateur. Vos informations d’identification n’ont pas été répertoriées dans VLSC.](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Si vous êtes le contact principal ou le destinataire des notifications et que vous n’avez pas terminé le processus d’intégration, vous devez suivre les étapes du scénario un afin de configurer de votre organisation.

Les sections suivantes fournissent plus de détails sur chacun de ces scénarios.

## <a name="onboarding-not-completed-by-primary-contact"></a>Intégration pas achevée par le contact principal

Si le contact principal n’a pas terminé l’expérience d’intégration, l’écran ci-dessous s’affiche. Si vous avez accès au [Centre de gestion des licences en volume (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), vous pouvez exécuter ce processus et accéder à la gestion des abonnements. Vous aurez besoin du [numéro de client public (PCN)](find-pcn.md) de votre organisation, qui se trouve dans le VLSC.

Dans le champ PCN, entrez le [PCN](find-pcn.md), puis sélectionnez **Envoyer un e-mail d’invitation**.
> [!div class="mx-imgBorder"]
> ![Capture d’écran du portail d’administration des abonnements Visual Studio](_img/post-migration-onboarding/send-invitation.png)

Vous recevez un e-mail contenant un lien unique pour terminer le processus d’intégration. Cliquez sur le lien dans l’e-mail, connectez-vous avec votre adresse de messagerie, puis entrez à nouveau le PCN. Le lien unique dans l’e-mail est ce qui vous permet d’accéder au portail d’administration des abonnements Visual Studio. Vous pouvez ensuite accéder aux abonnements et les gérer.
> [!div class="mx-imgBorder"]
> ![Capture d’écran de la notification de réussite](_img/post-migration-onboarding/email-success.png)

## <a name="primary-contact-did-not-provide-you-administrator-access"></a>Le contact principal ne vous n’a pas autorisé l’accès en tant qu’administrateur

Si votre contact principal a terminé le processus d’intégration et que vos informations d’identification se trouvaient précédemment dans le VLSC, mais que le contact principal ne vous y a pas donné accès, vous verrez la notification suivante. Pour devenir un administrateur, contactez l’un des super administrateurs de votre organisation qui s’affichent dans la notification.
> [!div class="mx-imgBorder"]
> ![Capture d’écran du portail d’administration des abonnements Visual Studio, avec la liste des super administrateurs](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Vos informations d’identification n’étaient pas répertoriées dans le VLSC avant la migration

Si votre contact principal a terminé l’intégration, mais ne vous a pas ajouté en tant qu’utilisateur et que vos informations d'identification n’étaient préalablement pas répertoriées dans le VLSC, vous verrez la notification suivante. Contactez votre [contact principal](find-primary-contact.md) pour accéder au portail.
> [!div class="mx-imgBorder"]
> ![Capture d’écran du portail d’administration des abonnements Visual Studio, avec la notification « vous êtes introuvable »](_img/post-migration-onboarding/cant-find-you.png)