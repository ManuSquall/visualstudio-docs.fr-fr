---
title: "Utilisation du portail d’administration | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to manage your organization's Visual Studio subscriptions with the Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: cf44f74b32bd830c613adcc1ee35a95b97636772
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Utilisation du portail d’administration des abonnements Visual Studio

Quand vous utilisez le portail d’administration des abonnements Visual Studio, gardez à l’esprit les points suivants :
 
- **Les abonnements Visual Studio sont fournis avec une licence par utilisateur.** Chaque abonné peut utiliser les logiciels sur un nombre illimité d’ordinateurs à des fins de développement et de test. 
- **Attribuez un seul niveau d’abonnement à chaque abonné**, en fonction de l’abonnement Visual Studio que votre organisation a acheté. Si des abonnés ont plusieurs niveaux d’abonnement, modifiez leurs paramètres de sorte qu’un seul niveau d’abonnement leur soit attribué. 
- **Le niveau d’abonnement d’un abonné doit être mis à jour** quand l’abonnement est mis à niveau (après l’achat d’une licence de niveau supérieur) ou renouvelé à un niveau inférieur. 
- **Ne partagez pas d’abonnements entre abonnés.** Vous devez attribuer un abonnement à chaque personne qui utilise la totalité ou une partie des avantages de l’abonnement (logiciels de développement et de test, Microsoft Azure, eLearning, etc.). 

## <a name="adminstrator-roles"></a>Rôles d’administrateur
Dans le nouveau portail d’administration des abonnements Visual Studio, deux rôles sont disponibles pour les clients de licence en volume. Ces rôles s’apparentent au rôle Contact principal/Destinataire des avis et au rôle Gestionnaire d’abonnements disponibles dans VLSC. 

**Super administrateurs** : à la création d’une organisation, le contact principal ou destinataire des avis devient super administrateur par défaut. Le contact principal ou destinataire des avis peut choisir d’assigner des super administrateurs ou administrateurs supplémentaires. Un super administrateur peut ajouter et supprimer d’autres administrateurs, ainsi que des abonnés. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en garder au minimum deux pour des raisons de sécurité. 

**Administrateurs** : un administrateur peut uniquement être assigné par un super administrateur. Il peut gérer les abonnés dans les contrats que le super administrateur leur attribue. 

## <a name="getting-started"></a>Commencer
### <a name="onboarding"></a>Intégration
Quand votre organisation est prête à être intégrée au portail d’administration des abonnements Visual Studio, un e-mail est envoyé au contact principal et au destinataire des avis pour les inviter à effectuer le processus d’intégration. Les étapes de l’intégration au nouveau portail sont décrites ci-dessous. Pour connaître la procédure pas à pas à suivre, regardez cette [vidéo sur l’intégration au portail d’administration](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) ou consultez cet [article du support technique](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Processus de migration vers le portail d’administration des abonnements Visual Studio").   
1.  **Recherche de votre numéro de client public (PCN) et connexion :**
    - Dans l’e-mail, le contact principal et le destinataire des avis sont indiqués avec un lien unique et avec les trois derniers chiffres de leur numéro de client public (PCN). * 
    - Pour obtenir le PCN complet, le contact principal doit se connecter au centre VLSC (des instructions pour rechercher le PCN y sont fournies). 
    - Une fois qu’ils ont trouvé leur PCN, les contacts doivent sélectionner leur lien unique qui les invite à se connecter. Ils peuvent se connecter à l’aide d’un compte professionnel ou scolaire si votre organisation est sur AAD ou avec un compte Microsoft (MSA) si votre organisation n’est pas sur AAD. 
    - Ils doivent ensuite entrer leur PCN. 
2.  **Assignation des administrateurs.** Après avoir entré leur PCN, les contacts sont inscrits comme super administrateurs dans le nouveau système, ce qui leur donne le droit d’ajouter d’autres super administrateurs et administrateurs (auparavant appelés gestionnaires d’abonnements). Pour éviter de perdre l’accès, cette étape doit être effectuée avant la date de migration de votre organisation. 
3.  **Accès au nouveau portail d’administration des abonnements.**  Après la migration de votre organisation, des e-mails sont envoyés aux nouveaux super administrateurs et administrateurs pour les inviter à accéder au nouveau portail et à commencer la gestion des abonnements.  

* *Remarque : Si le contact principal ou le destinataire des avis reçoivent plusieurs e-mails, cela signifie qu’ils ont plus d’un PCN. Ils doivent alors effectuer le processus en utilisant le lien unique correspondant au PCN référencé dans chaque e-mail.*

Si vous devez être ajouté au nouveau portail d’administration des abonnements Visual Studio, mais que vous ne savez pas qui est votre contact principal ou destinataire des avis, connectez-vous à [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) pour rechercher cette information. Consultez [cet article](https://www.visualstudio.com/subscriptions/support/locate-primary-contact/ "Comment localiser mon « Contact Principal » ?") pour connaître les étapes à suivre pour trouver votre contact principal ou destinataire des avis dans VLSC.
Si vous avez déjà été assigné comme administrateur, vous pouvez accéder directement au [portail d’administration des abonnements Visual Studio](https://manage.visualstudio.com).

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

![Page Abonnés dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Présentation de la page Détails
Pour obtenir plus d’informations sur le contrat affiché, sélectionnez l’onglet Détails. Cet onglet indique le statut du contrat, le compte d’achat, des détails sur l’organisation, les contacts principaux (VLSC), les super administrateurs (le cas échéant) et d’autres informations utiles.

![Page Détails dans le portail d’administration des abonnements Visual Studio](_img/using-admin-portal/details-page.png)

