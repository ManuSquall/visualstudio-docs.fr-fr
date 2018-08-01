---
title: Intégration dans le portail d’administration des abonnements Visual Studio après la migration de votre organisation
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c6f0f3de58f2f9f7d532a7b1b84520644fbdb1c7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234771"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>Intégration dans le portail d’administration des abonnements Visual Studio après la migration de votre organisation 

Si vous avez géré les abonnements Visual Studio dans le centre de gestion des licences en volume (VLSC) et que vous avez récemment visité le site pour gérer des abonnements, vous remarquerez que la gestion des abonnements n’est plus disponible dans le VLSC. Votre processus de gestion des abonnements devait ressembler à ça :

![Abonnements VLSC](_img/post-migration-onboarding/vlsc-subscriptions.png)

En arrivant à la page des abonnements, vous cliquiez probablement sur le lien ci-dessous. 

![Lien de résumé des relations](_img/post-migration-onboarding/relationship-summary-link.png)

Auparavant, vous seriez arrivé sur la page où vous pouviez gérer les abonnements.   Toutefois, les abonnements sont désormais gérés via un nouveau portail appelé portail d’administration abonnements Visual Studio.  Plusieurs étapes doivent être franchies par le contact principal ou le destinataire des notifications pour le contrat de licence en Volume de votre organisation. Si le contact principal ou le destinataire des notifications n’ont pas suivi ce processus ou ne sont plus disponibles, plusieurs scénarios sont possibles. Les éléments suivants vous guident a à travers les étapes à suivre pour accéder à la gestion des abonnements. 

Vous pouvez rencontrer un des cas suivants :
1.  [Le contact principal n’a pas terminé le processus d’intégration](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [Le contact principal a effectué l’intégration, mais ne vous a pas ajouté en tant qu’administrateur.  Vos informations d’identification ont été répertoriées dans VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [Le contact principal a effectué l’intégration, mais ne vous a pas ajouté en tant qu’administrateur, et vos informations d’identification n’ont pas été répertoriées dans le centre VLSC.](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Si vous êtes le contact principal ou le destinataire des notifications et que vous n’avez pas terminé le processus d’intégration, vous devez suivre les étapes du scénario un afin de configurer de votre organisation. 

Les éléments suivants sont des exemples d’écrans que vous pouvez vous attendre à voir et des étapes que vous pouvez suivre pour chacun des scénarios. 

## <a name="onboarding-not-completed-by-primary-contact"></a>Intégration pas achevée par le contact principal

Si le contact principal n’a pas terminé l’expérience d’intégration, attendez-vous à voir l’écran ci-dessous. Si vous avez accès au [Centre de gestion des licences en volume (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), vous serez en mesure d’exécuter ce processus et d’accéder à la gestion des abonnements. Vous aurez besoin du [numéro de client Public (PCN)](find-pcn.md) de votre organisation, qui se trouve dans le VLSC. 

Si le contact principal n’a pas terminé le processus d’intégration, il suffit d’entrer le [PCN](find-pcn.md) dans le champ et de sélectionner « Envoyer une invitation ». 

![Envoyer l'e-mail d’invitation](_img/post-migration-onboarding/send-invitation.png)

Une fois que vous avez cliqué sur le bouton pour envoyer l’invitation, vous recevrez un e-mail contenant un lien unique pour terminer le processus d’intégration. Vous devrez cliquer sur le lien dans l’e-mail, vous connecter avec votre adresse de messagerie, puis entrer à nouveau le PCN. Le lien unique dans l’e-mail est ce qui vous permet d’accéder au portail d’administration des abonnements Visual Studio. Vous pourrez alors accéder aux abonnements et le gérer. 

![Réussite de l’e-mail](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>Le contact principal ne vous n’a pas autorisé l’accès en tant qu’administrateur

Si votre contact principal a terminé le processus d’intégration et que vos informations d’identification se trouvaient précédemment dans le VLSC, mais que le contact principal ne vous y a pas donné accès, vous verrez la notification suivante une fois connecté au [portail d’administration des abonnements Visual Studio](https://manage.visualstudio.com/).  Pour devenir un administrateur, vous devrez contacter l’un des super administrateurs de votre organisation qui s’affichent sur l’écran.

![Liste des administrateurs](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Vos informations d’identification n’étaient pas répertoriées dans le VLSC avant la migration

Si votre contact principal a terminé l’intégration, mais ne vous a pas ajouté en tant qu’utilisateur et que vos informations d'identification n’étaient préalablement pas répertoriées dans le VLSC, vous verrez la notification ci-dessous lorsque vous tenterez d’accéder au [portail d’administration des abonnements Visual Studio](https://manage.visualstudio.com/). Vous devrez contacter votre [Contact principal](find-primary-contact.md) pour accéder au portail. 

![Impossible de vous trouver](_img/post-migration-onboarding/cant-find-you.png)