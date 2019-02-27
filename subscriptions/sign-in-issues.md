---
title: Problèmes de connexion aux abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: Découvrez les problèmes qui peuvent se produire lors de la connexion aux abonnements Visual Studio.
searchscope: VS Subscription
ms.openlocfilehash: 0073ec4193190e56fb5147b5da56898e1a289fd5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840946"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problèmes de connexion aux abonnements Visual Studio
Pour utiliser votre abonnement Visual Studio, vous devez tout d’abord vous connecter.  En fonction de votre abonnement, vous l’aurez peut-être configuré avec un compte Microsoft (MSA) ou une identité Azure Active Directory (AAD).  Cet article décrit certains problèmes que vous pouvez rencontrer lors de la connexion à votre abonnement.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Les comptes Microsoft (MSA) ne peuvent pas être créés avec des adresses e-mail professionnelles ou scolaires

La capacité à créer un nouveau compte Microsoft (MSA) personnel à l’aide d’une adresse e-mail professionnelle ou scolaire n’est plus autorisée quand le domaine de messagerie est configuré dans Azure AD. Qu’est-ce que cela signifie ? Si votre organisation utilise Office 365 ou d’autres services professionnels de Microsoft qui reposent sur Azure AD, et si vous avez ajouté un nom de domaine à votre locataire Azure AD, les utilisateurs ne pourront plus créer de compte Microsoft personnel à l’aide d’une adresse e-mail dans votre domaine.

### <a name="why-was-this-change-made"></a>Quelle est la raison de ce changement ?

Avoir un compte Microsoft personnel avec une adresse professionnelle comme nom d’utilisateur peut générer de nombreux problèmes pour les utilisateurs finaux comme pour les services informatiques. Par exemple :
- Les utilisateurs peuvent penser que leur compte Microsoft personnel est conforme aux normes de l’entreprise et qu’ils sont en conformité quand ils enregistrent un document professionnel dans leur OneDrive.
- Les utilisateurs qui quittent une organisation perdent généralement l’accès à leur adresse e-mail professionnelle. Dans ce cas, ils risquent de ne pas pouvoir se connecter à leur compte Microsoft personnel s’ils oublient leur mot de passe. L’inconvénient est que leur service informatique pourrait réinitialiser leur mot de passe et accéder au compte personnel d’anciens employés.
- Les services informatiques ont une fausse idée de la sécurité et de la propriété des comptes. En fait, il suffit aux utilisateurs d’effectuer un aller-retour d’un code à leur adresse e-mail professionnelle pour pouvoir renommer leur compte à tout moment.

La situation est particulièrement déroutante pour les utilisateurs qui ont deux comptes avec la même adresse e-mail (un dans Azure AD et un compte Microsoft).

### <a name="what-does-this-experience-look-like"></a>Quelle est l’expérience observée ?

Si vous tentez de vous inscrire à une application consommateur Microsoft avec une adresse e-mail professionnelle ou scolaire, vous recevez le message ci-dessous.

   > [!div class="mx-imgBorder"]
   > ![Impossible de créer un compte avec une adresse e-mail professionnelle](_img/sign-in-issues/cannot-use-work-email.png)

Toutefois, si vous tentez de vous inscrire à une application consommateur Microsoft qui prend en charge les comptes personnels et professionnels/scolaires, vous devriez recevoir ce message :

   > [!div class="mx-imgBorder"]
   > ![Comptes professionnels/scolaires pris en charge](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Les comptes existants sont-ils affectés ?
Le bloc d’inscription décrit ici empêche uniquement la création de nouveaux comptes. Il n’a aucun impact sur les utilisateurs qui ont déjà un compte Microsoft avec une adresse e-mail professionnelle/scolaire. Si vous êtes déjà dans cette situation, nous avons simplifié le renommage de compte Microsoft personnel. Cet [article du support technique](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) fournit des instructions pas à pas simples. Le renommage de votre compte Microsoft personnel implique de changer le nom d’utilisateur, et n’affecte pas votre adresse e-mail professionnelle ni votre mode de connexion aux services d’entreprise tels qu’Office 365. Cela n’affecte pas non plus vos informations personnelles, mais change uniquement la façon de vous y connecter. Vous pouvez utiliser une autre adresse e-mail (personnelle), obtenir une nouvelle adresse e-mail @outlook.com auprès de Microsoft, ou utiliser votre numéro de téléphone comme nouveau nom d’utilisateur.

> [!NOTE]
> Si votre service informatique vous a demandé de créer un compte Microsoft personnel avec votre e-mail professionnel ou scolaire, par exemple pour accéder à des services Microsoft tels que Support Premier, discutez avec votre équipe d’administration avant de renommer votre compte.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>La suppression d’une adresse de connexion peut empêcher l’accès à un abonnement

Si vous supprimez une ou plusieurs identités (MSA ou AAD) associées à votre abonnement, vos informations d’abonné (notamment votre nom d’utilisateur et ID de connexion) peuvent être rendues anonymes, entraînant la perte d’accès à votre abonnement.

Pour éviter tout impact sur votre accès à l’abonnement, utilisez l’une de ces techniques :
- Déployez un système de gestion d’identité unique, AAD ou MSA mais pas les deux
- Associez les identités AAD et MSA par le biais du locataire.


## <a name="next-steps"></a>Étapes suivantes
- Découvrez comment [lier des comptes MSA et AAD](/azure/active-directory/b2b/add-users-administrator) dans AAD.
- Apprenez-en davantage plus sur l’[anonymisation](anonymization.md).
