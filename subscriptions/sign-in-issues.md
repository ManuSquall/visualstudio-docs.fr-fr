---
title: Problèmes de connexion aux abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 10/28/2020
ms.topic: conceptual
description: Découvrez les problèmes qui peuvent se produire lors de la connexion aux abonnements Visual Studio.
ms.openlocfilehash: cf89d2deff2a5e9e81d065fbb7efda8097102d03
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903446"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problèmes de connexion aux abonnements Visual Studio
Pour utiliser votre abonnement Visual Studio, vous devez tout d’abord vous connecter.  En fonction de votre abonnement, vous l’aurez peut-être configuré avec un compte Microsoft (MSA) ou une identité Azure Active Directory (AAD).  Cet article décrit certains problèmes que vous pouvez rencontrer lors de la connexion à votre abonnement.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Les comptes Microsoft (MSA) ne peuvent pas être créés avec des adresses e-mail professionnelles ou scolaires
La capacité à créer un nouveau compte Microsoft (MSA) personnel à l’aide d’une adresse e-mail professionnelle ou scolaire n’est plus autorisée quand le domaine de messagerie est configuré dans Azure AD. Qu’est-ce que cela signifie ? Si votre organisation utilise Microsoft 365 ou d’autres services professionnels de Microsoft qui reposent sur Azure AD, et si vous avez ajouté un nom de domaine à votre locataire Azure AD, les utilisateurs ne seront plus en mesure de créer une compte Microsoft personnelle à l’aide d’une adresse de messagerie dans votre domaine.

### <a name="why-was-this-change-made"></a>Quelle est la raison de ce changement ?
Avoir un compte Microsoft personnel avec une adresse professionnelle comme nom d’utilisateur peut générer de nombreux problèmes pour les utilisateurs finaux comme pour les services informatiques. Par exemple :
- Les utilisateurs peuvent penser que leur compte Microsoft personnel est conforme aux normes de l’entreprise et qu’ils sont en conformité quand ils enregistrent un document professionnel dans leur OneDrive.
- Les utilisateurs qui quittent une organisation perdent généralement l’accès à leur adresse e-mail professionnelle. Dans ce cas, ils risquent de ne pas pouvoir se connecter à leur compte Microsoft personnel s’ils oublient leur mot de passe. L’inconvénient est que leur service informatique pourrait réinitialiser leur mot de passe et accéder au compte personnel d’anciens employés.
- Les services informatiques ont une fausse idée de la sécurité et de la propriété des comptes. En fait, il suffit aux utilisateurs d’effectuer un aller-retour d’un code à leur adresse e-mail professionnelle pour pouvoir renommer leur compte à tout moment.

La situation est particulièrement déroutante pour les utilisateurs qui ont deux comptes avec la même adresse e-mail (un dans Azure AD et un compte Microsoft).

### <a name="what-does-this-experience-look-like"></a>Quelle est l’expérience observée ?
Si vous tentez de vous inscrire à une application consommateur Microsoft avec une adresse e-mail professionnelle ou scolaire, vous recevez le message ci-dessous.

   > [!div class="mx-imgBorder"]
   > ![Impossible de créer un compte avec une adresse e-mail professionnelle](_img/sign-in-issues/cannot-use-work-email.png "Fournissez un nom d’utilisateur et un mot de passe pour créer votre compte.")

Toutefois, si vous tentez de vous inscrire à une application consommateur Microsoft qui prend en charge les comptes personnels et professionnels/scolaires, vous devriez recevoir ce message :

   > [!div class="mx-imgBorder"]
   > ![Comptes professionnels/scolaires pris en charge](_img/sign-in-issues/existing-account.png "Vous ne pouvez pas vous inscrire ici avec une adresse e-mail professionnelle ou scolaire...")

### <a name="are-existing-accounts-affected"></a>Les comptes existants sont-ils affectés ?
Le bloc d’inscription décrit ici empêche uniquement la création de nouveaux comptes. Il n’a aucun impact sur les utilisateurs qui ont déjà un compte Microsoft avec une adresse e-mail professionnelle/scolaire. Si vous êtes déjà dans cette situation, nous avons simplifié le renommage de compte Microsoft personnel. Cet [article du support technique](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) fournit des instructions pas à pas simples. L’attribution d’un nouveau nom à votre compte Microsoft personnel consiste à modifier le nom d’utilisateur et n’a aucun impact sur votre adresse de messagerie professionnelle ou sur la façon dont vous vous connectez aux services professionnels tels que Microsoft 365. Cela n’affecte pas non plus vos informations personnelles, mais change uniquement la façon de vous y connecter. Vous pouvez utiliser une autre adresse e-mail (personnelle), obtenir une nouvelle adresse e-mail @outlook.com auprès de Microsoft, ou utiliser votre numéro de téléphone comme nouveau nom d’utilisateur.

> [!NOTE]
> Si votre service informatique vous a demandé de créer un compte Microsoft personnel avec votre e-mail professionnel ou scolaire, par exemple pour accéder à des services Microsoft tels que Support Premier, discutez avec votre équipe d’administration avant de renommer votre compte.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>La suppression d’une adresse de connexion peut empêcher l’accès à un abonnement
Si vous supprimez une ou plusieurs identités (MSA ou AAD) associées à votre abonnement, vos informations d’abonné (notamment votre nom d’utilisateur et ID de connexion) peuvent être rendues anonymes, entraînant la perte d’accès à votre abonnement.

Pour éviter tout impact sur votre accès à l’abonnement, utilisez l’une de ces techniques :
- Déployez un système de gestion d’identité unique, AAD ou MSA mais pas les deux
- Associez les identités AAD et MSA par le biais du locataire.

## <a name="signing-in-may-fail-when-using-aliases"></a>La connexion risque de ne pas fonctionner en cas d’utilisation d’alias
Selon le type de compte utilisé pour la connexion, les abonnements disponibles peuvent ne pas s’afficher correctement lors de la connexion à [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Ce cas peut se produire si l’utilisateur emploie des « alias » ou des « noms conviviaux » au lieu de l’identité de connexion à laquelle l’abonnement est affecté. On parle ici d’utilisation d’alias.

### <a name="what-is-aliasing"></a>Qu’est-ce que l’utilisation d’alias ?
L’utilisation d’alias fait référence aux utilisateurs qui emploient des identités différentes pour se connecter à Windows (ou à leur compte Active Directory) et accéder à leur messagerie électronique.

Une entreprise peut par exemple posséder un service en ligne Microsoft pour sa connexion active (comme JohnD@contoso.com), mais les utilisateurs accèdent à leurs comptes de messagerie à l’aide d’alias ou de noms conviviaux (comme John.Doe@contoso.com). Pour de nombreux clients qui gèrent leurs abonnements à travers le Centre de gestion des licences en volume (VLSC), cela peut se traduire par un échec de la connexion, car l’adresse e-mail fournie (John.Doe@contoso.com) ne correspond pas à l’adresse d’annuaire (JohnD@contoso.com) requise pour une authentification correcte via l’option « Compte professionnel ou scolaire ».

### <a name="what-options-do-i-have"></a>Quelles sont les options dont je dispose ?
Du point de vue de l’abonné, il est important de commencer par travailler avec votre administrateur pour comprendre la configuration des identités de votre entreprise. Si nécessaire, votre administrateur devra peut-être mettre à jour les paramètres de votre compte à partir de son portail d’administration, ou vous devrez peut-être créer un compte Microsoft (MSA) à l’aide de votre adresse e-mail d’entreprise. Avant de suivre les étapes de création d’un MSA, contactez votre administrateur en ce qui concerne les stratégies ou problèmes liés à l’exécution de cette action. 

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Découvrez comment [lier des comptes MSA et AAD](/azure/active-directory/b2b/add-users-administrator) dans AAD.
- Apprenez-en davantage plus sur l’[anonymisation](anonymization.md).