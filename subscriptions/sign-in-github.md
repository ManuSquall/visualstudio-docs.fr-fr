---
title: Connexion aux abonnements Visual Studio avec votre compte GitHub | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/05/2021
ms.topic: conceptual
description: Découvrez comment vous connecter à vos abonnements Visual Studio avec votre compte GitHub.
ms.openlocfilehash: 41966fb4468832b3e1a320e898164989d1fb5c3b
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249734"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Connexion à vos abonnements Visual Studio avec votre compte GitHub 

Les étapes de connexion à votre abonnement Visual Studio varient selon le type de compte que vous utilisez. Par exemple, vous utilisez peut-être un compte Microsoft (MSA) ou une adresse e-mail fournie par votre employeur ou votre établissement scolaire. Depuis janvier 2019, vous pouvez aussi utiliser votre compte GitHub pour vous connecter à certains abonnements. 

Cet article décrit les étapes à suivre pour vous connecter avec votre compte GitHub.

## <a name="signing-in-with-your-github-account"></a>Connexion avec votre compte GitHub

Compte tenu de la prise en charge des identités GitHub, vous pouvez vous servir de votre compte GitHub existant comme informations d’identification pour un compte Microsoft existant ou nouveau. Votre compte GitHub est alors lié à votre compte Microsoft. 

Quand vous vous connectez avec GitHub, Microsoft vérifie si les adresses e-mail associées à votre compte GitHub correspondent à un compte Microsoft personnel ou d’entreprise existant. Si l’adresse correspond à votre compte d’entreprise, vous êtes invité à vous connecter à ce compte. Si l’adresse correspond à un compte personnel, votre compte GitHub est ajouté comme méthode de connexion à ce compte personnel.

Une fois que les informations d’identification de vos comptes Microsoft et GitHub sont liées, vous pouvez utiliser ce mode d’authentification unique partout où un compte Microsoft personnel peut être utilisé, comme les sites Azure, les applications Office et Xbox. Ces comptes peuvent aussi servir de compte Microsoft pour les connexions invitées Azure Active Directory, à supposer que l’adresse e-mail correspond à celle de l’invitation.

> [!NOTE]
> En liant une identité GitHub à un compte Microsoft, vous ne communiquez aucun code d’accès à Microsoft. Quand des applications comme Azure DevOps et Visual Studio nécessitent un accès à vos dépôts de code, vous êtes invité à accorder un consentement spécifique pour cet accès. 

### <a name="frequently-asked-questions"></a>Forum aux questions
Les questions fréquentes (FAQ) suivantes répondent aux questions que vous pouvez vous poser concernant l’utilisation des informations d’identification de votre compte GitHub pour vous connecter à des abonnements Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>Q : J’ai oublié mon mot de passe GitHub.  Comment puis-je accéder à mon compte maintenant ?
R : vous pouvez récupérer votre compte GitHub en accédant à [Réinitialiser votre mot de passe](https://github.com/password_reset). Vous pouvez aussi récupérer votre compte Microsoft lié à GitHub en entrant l’adresse e-mail de votre compte GitHub dans le fenêtre [Récupérer votre compte](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>Q : J’ai supprimé mon compte GitHub.  Comment puis-je accéder à mon compte de service administré (MSA) Microsoft maintenant ?
R : Si vous n’avez pas d’autres informations d’identification sur votre MSA (comme un mot de passe, une application authentificateur ou une clé de sécurité), vous pouvez récupérer votre compte Microsoft à l’aide de l’adresse de messagerie qui lui est associée. Pour commencer, accédez à [Récupérer votre compte](https://account.live.com/password/reset). Vous devez ajouter un mot de passe à votre compte qui déterminera ainsi la façon dont vous serez connecté par la suite. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>Q : il n’existe pas d’option « se connecter avec GitHub » sur la page de connexion.  Comment puis-je utiliser mes informations d’identification GitHub pour me connecter ?
R : tapez l’adresse de messagerie du compte GitHub que vous avez choisie lors de la création de votre compte Microsoft lié à GitHub. Nous vous rechercherons et vous renverrons vers GitHub pour vous connecter. Autrement, si la page de connexion comporte un lien Options de connexion, utilisez le bouton **Se connecter avec GitHub** qui s’affiche après avoir cliqué sur ce lien. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>Q : je ne parviens pas à me connecter à certains de mes applications et produits avec GitHub.  Pourquoi ?
R : tous les produits Microsoft ne peuvent pas accéder à GitHub.com à partir de leur page de connexion, par exemple, les consoles Xbox. Ainsi, quand vous tapez l’adresse e-mail de votre compte GitHub lié, nous vous envoyons un code à cette adresse pour vérifier qu’il s’agit bien de vous. Vous vous connectez toujours au même compte, mais en employant une autre méthode de connexion. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>Q : J’ai ajouté un mot de passe au compte Microsoft que j’ai lié à mon compte GitHub.  Cela va-t-il causer un problème ?
R : pas du tout. Cela ne changera pas votre mot de passe GitHub ; simplement, vous vous connecterez à votre compte Microsoft d’une autre façon. Chaque fois que vous vous connecterez en utilisant votre adresse e-mail, nous vous offrirons le choix de vous connecter avec le mot de passe de votre compte Microsoft ou d’aller sur GitHub pour vous connecter. Si vous avez besoin d’ajouter un mot de passe, nous recommandons vivement d’en utiliser un différent de celui de votre compte GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>Q : Je souhaite ajouter l’application Authenticator au compte que j’ai créé à l’aide de GitHub.  Est-ce possible ?
R : aucun problème : il vous suffit de télécharger l’application et de vous connecter à l’aide de votre adresse e-mail. Au moment de vous connecter avec votre adresse e-mail, vous serez invité à choisir l’[application d’authentification](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) ou GitHub comme informations d’identification.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Q : J’ai activé l’authentification à deux facteurs sur mes comptes GitHub et Microsoft (MSA), mais lorsque je me connecte à mon MSA, je suis toujours invité à s’authentifier deux fois.  Pourquoi ?
R : en raison des restrictions de sécurité, Microsoft compte la connexion avec GitHub en tant que vérification à facteur unique, même si la vérification en deux étapes est activée. Par conséquent, vous devez vous réauthentifier pour votre compte Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Q : Comment savoir si mes comptes compte Microsoft et GitHub sont liés ?
R : chaque fois que vous vous connectez à l’aide de votre alias de compte (adresse e-mail, numéro de téléphone, nom Skype), nous vous présenterons toutes les méthodes de connexion de votre compte. Si GitHub ne vous est pas proposé, c’est que vous ne l’avez pas encore configuré.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Q : Comment puis-je dissocier mes comptes Microsoft et GitHub ? 
R : accédez à l' [onglet sécurité](https://account.microsoft.com/security) de Account.Microsoft.com, puis cliquez sur **options de sécurité avancées** pour dissocier votre compte github. En dissociant votre compte GitHub, vous le soustrayez des méthodes de connexion et supprimez l’accès aux dépôts GitHub dans Visual Studio. Il est possible que d’autres produits Microsoft aient demandé un accès séparé à votre compte GitHub. Autrement dit, si vous supprimez l’accès ici, l’accès ne sera pas pour autant supprimé dans tous les produits. Accédez à la page [application permissions](https://github.com/settings/applications) de votre profil GitHub pour révoquer le consentement des applications listées dans cette page.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Q : J’essaie d’utiliser mon compte GitHub pour me connecter, mais je suis invité à indiquer que j’ai déjà une identité Microsoft que je dois utiliser à la place.  Que se passe-t-il ?
R : Si vous avez une adresse de messagerie Azure Active Directory sur votre compte GitHub, cela signifie que vous disposez déjà d’une identité Microsoft qui peut accéder à Azure et exécuter des pipelines CI à l’aide de votre code GitHub. L’utilisation de ce compte est l’assurance que vos ressources et pipelines de build Azure restent dans les limites de votre organisation. Cependant, si vous effectuez un travail personnel, nous vous recommandons de placer une adresse e-mail personnelle sur votre compte GitHub, vous y aurez ainsi toujours accès. Après quoi, essayez à nouveau de vous connecter et choisissez **Utiliser une autre adresse de messagerie** quand vous êtes invité à vous connecter à votre compte professionnel ou scolaire. Cela vous permettra de créer un compte Microsoft avec cette adresse e-mail personnelle.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que vous avez réussi à vous connecter au portail des abonnements, nous vous recommandons de consulter la page Avantages à l’adresse https://my.visualstudio.com/benefits, et d’explorer les outils, services et offres disponibles.