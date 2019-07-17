---
title: Questions fréquentes (FAQ) sur la migration de l’administration du Centre VLSC | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: conceptual
description: Questions fréquentes (FAQ) sur la migration de l’administration du Centre de gestion des licences en volume
ms.openlocfilehash: 34c5d2d287507699ebc47bdd7e4716838c408d07
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784755"
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Migration de l’administration des abonnements Visual Studio

Dans les prochains mois, des changements vont être apportés à la gestion des abonnements Visual Studio (anciennement Abonnements MSDN). Aujourd’hui, vous pouvez acheter des abonnements Visual Studio via le programme de licence en volume et les gérer dans le portail du Centre VLSC (Volume License Service Center). Un nouveau portail de gestion est en cours de création et les abonnements Visual Studio seront gérés dans ce nouveau portail. En plus des opérations existantes du Centre VLSC, le nouveau portail permettra les attributions en bloc illimitées, le suivi et le filtrage des abonnements, et donnera la possibilité d’utiliser Azure Active Directory (Azure AD) pour gérer les accès. Vous trouverez le nouveau portail d’administration de Visual Studio sur : [https://manage.visualstudio.com](https://manage.visualstudio.com).

> [!Note]
> Cette migration n’affectera pas les clients MPSA.

## <a name="frequently-asked-questions"></a>FAQ

### <a name="why-is-it-changing"></a>Pourquoi ce changement ?
Le nouveau portail optimisera l’expérience de gestion des abonnements Visual Studio et créera une même expérience de gestion des abonnements de Visual Studio, quelle que soit la façon dont ils ont été achetés. Le nouveau portail a une nouvelle plateforme qui permet d’utiliser Azure AD, ce qui nous positionne pour l’avenir. Il présente aussi une interface utilisateur mise à jour qui offre une navigation et une utilisation plus faciles, et améliore l’efficacité des administrateurs.

### <a name="who-will-be-impacted"></a>Qui est concerné ?
Le changement a un impact sur tous les clients qui ont des contrats de licence en volume actifs et qui ont acheté des abonnements Visual Studio via le programme de licence en volume.

### <a name="when-is-it-changing"></a>Quand aura lieu ce changement ?
Il s’agit d’une transition massive, qui sera effectuée par phases, jusqu’à ce que tous les clients ayant des contrats de licence en volume actifs pour des abonnements Visual Studio soient migrés vers le nouveau portail de gestion. La migration a commencé au cours du premier trimestre 2017. Nous avertirons nos clients de licence en volume à l’avance, une semaine avant leur migration prévue.

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>Mon organisation doit-elle s’inscrire à Azure Active Directory (Azure AD) ?
Votre organisation n’a pas besoin de s’inscrire à Azure AD, mais elle peut le faire à tout moment. Si vous choisissez d’intégrer Azure AD, vous pouvez le faire sans frais en utilisant le niveau gratuit pour Azure AD. Avec Azure Active Directory, vous pouvez protéger votre organisation avec une meilleure sécurité, un plus grand contrôle et une fiabilité à long terme. Cependant, si vous n’êtes pas prêt pour Azure AD, vous pouvez continuer à utiliser vos comptes Microsoft comme vous le faites aujourd’hui.

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>Comment savoir quand mon organisation sera migrée ?
Les contacts principaux et les contacts pour les notifications reçoivent un e-mail les invitant à effectuer le processus d’intégration une semaine avant la migration de votre organisation. Les gestionnaires d’abonnements reçoivent également un e-mail les informant que nous avons contacté les contacts principaux et les contacts pour les notifications, et que nous leur avons fourni des informations sur la façon de garantir la réussite de l’intégration. Découvrez comment [localiser les contacts principaux et les contacts pour les notifications de votre organisation](#how-do-i-find-out-who-my-primary-or-notices-contact-is).

### <a name="is-onboarding-different-from-migration"></a>L’intégration est-elle différente de la migration ?
Oui.  Ce processus est constitué de deux phases. Configurer (ou intégrer) votre organisation avant la migration garantit que votre travail d’administrateur ne sera pas interrompu. Une fois que nous avons migré les informations de votre organisation, vous pouvez gérer les abonnements Visual Studio dans le nouveau portail. Si les contacts principaux et les contacts pour les notifications n’effectuent pas l’intégration avant la migration, les gestionnaires d’abonnements sont bloqués et ne peuvent pas gérer les abonnements tant que le processus d’intégration n’a pas été effectué.

### <a name="what-is-the-onboarding-process"></a>Qu’est-ce que le processus d’intégration ?
Un e-mail est envoyé aux contacts principaux et aux contacts pour les notifications, les invitant à effectuer le processus d’intégration.
Voici des instructions sur le processus.
1. **Recherche de votre numéro de client public (PCN) et connexion :**

    a. Dans l’e-mail, les contacts principaux et les contacts pour les notifications sont indiqués avec un lien unique et les trois derniers chiffres de leur numéro PCN (Public Customer Number).*

    b. Pour obtenir le numéro PCN complet, le contact principal doit se connecter au Centre VLSC (vous pouvez trouver ci-dessous des instructions pour trouver le numéro PCN).

    c. Une fois qu’ils ont trouvé leur PCN, les contacts doivent sélectionner leur lien unique qui les invite à se connecter. Ils peuvent se connecter avec un compte professionnel ou scolaire (si votre organisation est sur Azure AD), ou avec un compte Microsoft (MSA) si votre organisation n’est pas sur Azure AD.

    d. Ils sont ensuite invités à entrer le numéro PCN.

2. **Configurez vos administrateurs :**

    Après avoir entré le numéro PCN, ils sont dirigés vers la page où ils peuvent ajouter des super administrateurs et des administrateurs (auparavant appelés gestionnaires d’abonnements). Dans l’idéal, ceci doit être effectué avant la date de la migration de votre organisation, de façon à éviter toute interruption dans la gestion de vos abonnements.

3. **Accès au nouveau portail de gestion des abonnements :** Après la migration de votre organisation, des e-mails sont envoyés aux super administrateurs et aux administrateurs pour les inviter à accéder au nouveau portail et à commencer à gérer les abonnements.

> [!NOTE]
> Si les contacts principaux ou les contacts pour les notifications reçoivent plusieurs e-mails, cela signifie qu’ils ont plusieurs numéros PCN. Ils doivent alors effectuer le processus en utilisant le lien unique correspondant au numéro PCN référencé dans chaque e-mail.

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>Qu’est la différence entre un super administrateur et un administrateur ?
Quand les contacts principaux et les contacts pour les notifications se connectent pour la première fois, ils sont automatiquement configurés en tant que super administrateurs. Les super administrateurs peuvent gérer l’accès des administrateurs aux abonnements en ajoutant/supprimant d’autres super administrateurs ou d’autres administrateurs, et peuvent aussi gérer les abonnements. Les super administrateurs peuvent choisir d’affecter d’autres super administrateurs en plus d’eux-mêmes.

Les administrateurs (précédemment appelés gestionnaires d’abonnement) peuvent seulement gérer les abonnements, mais ils ne peuvent pas contrôler qui a accès à la gestion des abonnements.

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>Comment vais-je, en tant qu’administrateur, intégrer le nouveau portail ?
Les contacts principaux et les contacts pour les notifications de votre organisation reçoivent un e-mail avec un lien unique, qui les amène à une page où ils peuvent se connecter avec des comptes professionnels ou scolaires, associés à un locataire Azure Active Directory (Azure AD) ou à des comptes Microsoft personnels. Une fois connectés, ils doivent entrer le numéro PCN ou le numéro d’autorisation de votre organisation pour vérifier les contrats. Ils sont ensuite configurés comme super administrateurs, autorisés à ajouter d’autres administrateurs, comme vous-même, pour gérer les abonnements Visual Studio.

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>Où gérer les abonnements si mon organisation a déjà été intégrée, mais n’a pas été migrée ?
Vous pouvez continuer à gérer les abonnements via le Centre VLSC jusqu’à réception de l’e-mail des abonnements Visual Studio indiquant que votre organisation a été migrée et peut maintenant être gérée dans le nouveau portail.

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>Où trouver le numéro PCN ou le numéro d’autorisation de mon organisation ?
Connectez-vous au [Centre VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx), puis accédez au chemin suivant : **Abonnements** > **Abonnements Visual Studio**. le numéro PCN se trouve sous les **Résultats pour le contrat/numéro de client public**. Vous trouverez des instructions pas à pas pour localiser votre PCN dans cet [article d’aide](find-pcn.md).

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>Comment trouver qui est mon contact principal ou mon contact pour les notifications ?
Connectez-vous au [Centre VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx), puis accédez au chemin suivant : **Licences > Liste des contrats**. Sélectionnez votre **Identifiant de contrat > Contacts**. Suivez les instructions pas à pas pour trouver votre contact principal ou votre contact pour les notifications dans cet [article d’aide](find-primary-contact.md).

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>Que se passe-t-il si mon contact principal ou mon contact pour les notifications est parti, ne fait plus partie de l’entreprise ou n’est pas disponible pour l’intégration ?
Vous devez [contacter le support technique](https://visualstudio.microsoft.com/subscriptions/support/#talktous) et fournir l’e-mail que vous avez utilisé dans le Centre VLSC pour la gestion des abonnements. Après vérification, le support technique peut vous aider pour le processus d’intégration.

### <a name="what-will-happen-with-renewing-customers"></a>Comment cela se passe avec les clients procédant à un renouvellement ?
Les clients effectuant un renouvellement doivent continuer à renouveler leurs abonnements comme d’habitude, car les processus de renouvellement ne sont pas impactés par la migration.

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>Mon organisation doit-elle attendre pour configurer un nouveau contrat dans le nouveau système, au lieu de renouveler un contrat existant ?
Non.  La migration n’affecte pas la création ou le renouvellement des contrats.

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>Que se passe-t-il si le contrat de mon organisation est dans la période de grâce pendant la transition ? L’organisation sera-t-elle également migrée ?
Oui, si le contrat est toujours actif, votre organisation sera migrée.

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>Que se passe-t-il si mon organisation a surutilisé des licences dans le système actuel ? Serons-nous migrés vers le nouveau système ?
Oui, votre organisation sera quand même migrée vers le nouveau système. La possibilité de surutiliser (pour les types de contrats qui le permettent) existe dans le nouveau système.

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>Que se passe-t-il si mon organisation a plusieurs abonnements attribués à un même utilisateur ou à une même adresse e-mail ?
Votre organisation sera quand même migrée.  Toutefois, vous ne pouvez pas affecter d’abonnements supplémentaires du même niveau (c’est-à-dire Enterprise, Professional, etc.) à cet utilisateur/cette adresse e-mail. Tous les abonnements du même niveau qui ont la même adresse e-mail seront toujours visibles après la migration, mais les administrateurs devront changer les adresses e-mail de façon à ce qu’elles soient uniques. Vous ne pourrez pas attribuer plusieurs abonnements du même niveau à un même utilisateur ou une même adresse e-mail dans le nouveau portail.

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>Où puis-je trouver les informations les plus récentes sur la migration ?
Pour obtenir les informations les plus récentes concernant cette migration, visitez notre [page web](https://aka.ms/vs-admin) sur l’administration des abonnements Visual Studio. Si vous avez besoin de support, consultez la [page de support](http://visualstudio.microsoft.com/subscriptions/support/#!collections/962-subscriptions) des abonnements Visual Studio, qui contient des informations d’aide autonome et des informations de contact de support. Au cours des prochains mois, nous continuerons à fournir des mises à jour sur la page web d’administration et par e-mail, pour que cette transition puisse se faire facilement.

## <a name="resources-and-support-information"></a>Ressources et informations de support
- [Page web d’administration](https://visualstudio.microsoft.com/subscriptions-administration/)

- [Support](https://visualstudio.microsoft.com/subscriptions/support/) pour les abonnements et la gestion Visual Studio

- [Guide pratique pour trouver mon PCN](find-pcn.md)

- [Guide pratique pour trouver votre contact principal ou votre contact pour les notifications](find-primary-contact.md)

- [Vidéo](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) sur l’intégration de votre organisation et la gestion des administrateurs
