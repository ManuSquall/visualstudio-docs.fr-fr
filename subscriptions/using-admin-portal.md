---
title: Utilisation du portail d’administration | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Découvrez comment gérer les abonnements Visual Studio de votre organisation dans le portail d’administration.
searchscope: VS Subscription
ms.openlocfilehash: ec741707f061de7e7173da9c4a07a50469cf50da
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843709"
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Utilisation du portail d’administration des abonnements Visual Studio

Quand vous utilisez le portail d’administration des abonnements Visual Studio, gardez à l’esprit les points suivants :

- **Les abonnements Visual Studio sont fournis avec une licence par utilisateur.** Chaque abonné peut utiliser les logiciels sur un nombre illimité d’ordinateurs à des fins de développement et de test.
- **Attribuez un seul niveau d’abonnement à chaque abonné**, en fonction de l’abonnement Visual Studio que votre organisation a acheté. Si des abonnés ont plusieurs niveaux d’abonnement, modifiez leurs paramètres de sorte qu’un seul niveau d’abonnement leur soit attribué.
- **Le niveau d’abonnement d’un abonné doit être mis à jour** quand l’abonnement est mis à niveau (après l’achat d’une licence de niveau supérieur) ou renouvelé à un niveau inférieur.
- **Ne partagez pas d’abonnements entre abonnés.** Vous devez attribuer un abonnement à chaque personne qui utilise la totalité ou une partie des avantages de l’abonnement (logiciels de développement et de test, Microsoft Azure, eLearning, etc.).

## <a name="administrator-roles"></a>Rôles d’administrateur

Dans le nouveau portail d’administration des abonnements Visual Studio, deux rôles sont disponibles pour les clients de licence en volume. Ces rôles s’apparentent au rôle Contact principal/Destinataire des avis et au rôle Gestionnaire d’abonnements disponibles dans VLSC.

**Super administrateurs :** au moment de la création d’une organisation, le contact principal ou le destinataire des notifications devient super administrateur par défaut. Le contact principal ou destinataire des avis peut choisir d’assigner des super administrateurs ou administrateurs supplémentaires. Un super administrateur peut ajouter et supprimer d’autres administrateurs, ainsi que des abonnés. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en garder au minimum deux pour des raisons de sécurité.

**Administrateurs :** un administrateur peut uniquement être créé par un super administrateur. Il peut gérer les abonnés dans les contrats que le super administrateur leur attribue.

## <a name="getting-started"></a>Bien démarrer

Si vous voulez utiliser le portail d’administration pour gérer les abonnements de votre organisation, vous devez d’abord intégrer votre organisation dans le portail.  Une fois que vous avez effectué l’intégration, vous pouvez vous familiariser avec les pages Abonnés et Détails, qui contiennent les outils et les informations nécessaires pour effectuer vos tâches de gestion des abonnements.

### <a name="onboarding"></a>Intégration

Quand votre organisation est prête à être intégrée au portail d’administration des abonnements Visual Studio, un e-mail est envoyé au contact principal et au destinataire des avis pour les inviter à effectuer le processus d’intégration. Les étapes de l’intégration au nouveau portail sont décrites ci-dessous. Pour connaître la procédure pas à pas à suivre, regardez cette [vidéo sur l’intégration au portail d’administration](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) ou consultez cet [article du support technique](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Processus de migration vers le portail d’administration des abonnements Visual Studio").
1.  **Recherche de votre numéro de client public (PCN) et connexion :**
    - Dans l’e-mail, le contact principal et le destinataire des avis sont indiqués avec un lien unique et avec les trois derniers chiffres de leur numéro de client public (PCN). *
    - Pour obtenir le PCN complet, le contact principal doit se connecter au centre VLSC (des instructions pour rechercher le PCN y sont fournies).
    - Une fois qu’ils ont trouvé leur PCN, les contacts doivent sélectionner leur lien unique qui les invite à se connecter. Ils peuvent se connecter à l’aide d’un compte professionnel ou scolaire si votre organisation est sur AAD ou avec un compte Microsoft (MSA) si votre organisation n’est pas sur AAD.
    - Ils doivent ensuite entrer leur PCN.
2.  **Assignation des administrateurs.** Après avoir entré leur PCN, les contacts sont inscrits comme super administrateurs dans le nouveau système, ce qui leur donne le droit d’ajouter d’autres super administrateurs et administrateurs (auparavant appelés gestionnaires d’abonnements). Pour éviter de perdre l’accès, cette étape doit être effectuée avant la date de migration de votre organisation.
3.  **Accès au nouveau portail d’administration des abonnements.**  Après la migration de votre organisation, des e-mails sont envoyés aux nouveaux super administrateurs et administrateurs pour les inviter à accéder au nouveau portail et à commencer la gestion des abonnements.

> [!NOTE]
> Si les contacts principaux ou les contacts pour les notifications reçoivent plusieurs e-mails, cela signifie qu’ils ont plusieurs numéros PCN. Ils doivent alors effectuer le processus en utilisant le lien unique correspondant au numéro PCN référencé dans chaque e-mail.*

Si vous devez être ajouté au nouveau portail d’administration des abonnements Visual Studio, mais que vous ne savez pas qui est votre contact principal ou destinataire des avis, connectez-vous à [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) pour rechercher cette information. Consultez la rubrique [Rechercher votre contact principal](find-primary-contact.md) pour savoir comment localiser votre contact principal ou votre contact pour les notifications dans le Centre VLSC.
Si vous avez déjà été configuré comme administrateur, vous pouvez accéder directement au [portail d’administration des abonnements Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Présentation de la page Abonnés
Une fois que vous avez attribué les abonnements, l’onglet Abonnés fournit des informations détaillées suivantes sur les abonnés :
- Nom et prénom des abonnés.
- Leur adresse e-mail.
- Niveau d’abonnement qui leur a été attribué.
- Date d’attribution de leur abonnement.
- Date d’expiration de leur abonnement.
- Texte descriptif facultatif.
- Indication de l’activation ou de la désactivation des téléchargements pour les abonnés.
- Pays dans lequel ils sont situés.
- Langue choisie pour l’e-mail de communication d’attribution envoyé par le portail d’administration.
- Champ facultatif indiquant une adresse e-mail pour les communications différente de celle pour la connexion.

Sur le côté gauche de cette page, vous pouvez voir des informations supplémentaires sur le nombre de licences d’abonnement achetées, attribuées et encore disponibles dans votre organisation pour chaque contrat.
> [!div class="mx-imgBorder"]
> ![Page Abonnés dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Présentation de la page Détails
Pour obtenir plus d’informations sur le contrat affiché, sélectionnez l’onglet Détails. Cet onglet indique le statut du contrat, le compte d’achat, des détails sur l’organisation, les contacts principaux (VLSC), les super administrateurs (le cas échéant) et d’autres informations utiles.
> [!div class="mx-imgBorder"]
> ![Page Détails dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/details-page.png)
