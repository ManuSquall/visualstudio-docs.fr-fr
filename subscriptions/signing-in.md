---
title: Connexion aux abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 05/14/2019
ms.topic: conceptual
description: Comment se connecter à votre abonnement Visual Studio
ms.openlocfilehash: acfd04dfdbbca78d9f139a507ddb9f34ae8f9475
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784927"
---
# <a name="signing-in-to-your-visual-studio-subscription"></a>Connexion à votre abonnement Visual Studio

Les étapes de connexion à votre abonnement Visual Studio varient selon le type de compte que vous utilisez.  Par exemple, vous utilisez peut-être un compte Microsoft (MSA) ou une adresse e-mail fournie par votre employeur ou votre établissement scolaire.  Depuis janvier 2019, vous pouvez aussi utiliser votre compte GitHub pour vous connecter à certains abonnements. 

Quatre méthodes de connexion différentes sont abordées dans cet article :  Utilisez les liens à droite pour accéder à l’une de ces sections.
1. Connexion avec votre compte Microsoft (MSA)
2. Connexion avec votre compte professionnel ou scolaire
3. Utilisation d’un compte Microsoft pour la connexion à un compte professionnel ou scolaire
4. Connexion avec votre compte GitHub

## <a name="signing-in-with-your-microsoft-account-msa"></a>Connexion avec votre compte Microsoft (MSA)
1. Consultez [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Entrez l’adresse e-mail que vous avez fournie lorsque vous avez configuré ou acheté votre abonnement Visual Studio.

   > [!NOTE]
   > Cette adresse est également identifiée dans l’e-mail de bienvenue à l’abonné que vous avez reçu lorsque vous avez acheté l’abonnement ou que vous vous êtes inscrit à Visual Studio Dev Essentials. Si vous avez des difficultés à localiser l’e-mail de bienvenue, vérifiez votre dossier de courrier indésirable.

3. Entrez votre mot de passe.
4. Cliquez sur **Connexion**.
5. À ce stade, la page « Avantages » doit être affichée.

### <a name="for-visual-studio-dev-essentials-users"></a>Pour les utilisateurs Visual Studio Dev Essentials :
Lorsque vous accédez à votre abonnement Visual Studio Dev Essentials pour la première fois, une boîte de dialogue de bienvenue s’affiche.  Cliquez sur **Confirmer** pour accepter les conditions générales du programme.

## <a name="signing-in-with-your-work-or-school-account"></a>Connexion avec votre compte professionnel ou scolaire

1. Consultez [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Entrez l’adresse e-mail qui est associée au nouvel abonnement Visual Studio.

   > [!NOTE]
   > Cette adresse est également indiquée dans le message de bienvenue à l’abonné que vous avez reçu. Si vous avez des difficultés à localiser l’e-mail de bienvenue, vérifiez votre dossier de courrier indésirable.

3. Cliquez sur **Continuer**.
4. Vous êtes redirigé vers la page de connexion de votre entreprise.
5. Entrez votre mot de passe.
6. Cliquez sur **Connexion**.
7. À ce stade, la page « Avantages » doit être affichée

Le type d’abonnement que vous utilisez s’affiche maintenant dans la barre bleue dans la partie supérieure du portail.

Vous pouvez également voir votre abonnement actuellement sélectionné dans le coin supérieur droit, sous votre nom d’utilisateur.  L’intitulé « Affichage : » suivi de l’abonnement s’affiche.  Si vous avez plusieurs abonnements, vous pouvez cliquer sur la flèche déroulante et sélectionner l’abonnement que vous souhaitez utiliser.

## <a name="using-your-microsoft-account-to-sign-in-to-a-work-or-school-account"></a>Utilisation de votre compte Microsoft pour la connexion à un compte professionnel ou scolaire

1. Accédez à [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Entrez l’adresse e-mail qui est associée au nouvel abonnement Visual Studio attribué

   > [!NOTE]
   > Cette adresse est également indiquée dans la lettre de bienvenue envoyée à l’abonné. Si vous n’avez pas reçu la lettre de bienvenue, vérifiez qu’elle n’est pas dans le dossier de courrier indésirable

3. Cliquez sur **Continuer**.
4. Vous allez être redirigé vers une page de sélection.
    - Sélectionnez **Compte professionnel ou scolaire** si l’abonnement est attribué à un compte « professionnel ou scolaire » qui est associé à un locataire Azure Active Directory (AAD).
    - Sélectionnez **Personnel** si l’abonnement est associé à une adresse e-mail « professionnelle », mais qu’il a également été converti en compte Microsoft (MSA) « personnel ».

        > [!NOTE]
        > C’est le cas pour de nombreux abonnés qui ont utilisé des abonnements Visual Studio (anciennement MSDN) par le passé.

    - Si un chemin d’accès échoue, essayez l’autre.  Il est possible que les administrateurs des abonnements aient modifié votre abonnement.

5. Entrez votre mot de passe.
6. Cliquez sur **Connexion**.
7. À ce stade, la page « Avantages » doit être affichée.

## <a name="signing-in-with-your-github-account"></a>Connexion avec votre compte GitHub

Compte tenu de la prise en charge des identités GitHub, vous pouvez vous servir de votre compte GitHub existant comme informations d’identification pour un compte Microsoft existant ou nouveau. Votre compte GitHub est alors lié à votre compte Microsoft. 

Quand vous vous connectez avec GitHub, Microsoft vérifie si les adresses e-mail associées à votre compte GitHub correspondent à un compte Microsoft personnel ou d’entreprise existant. Si l’adresse correspond à votre compte d’entreprise, vous êtes invité à vous connecter à ce compte. Si l’adresse correspond à un compte personnel, votre compte GitHub est ajouté comme méthode de connexion à ce compte personnel.

Une fois que les informations d’identification de vos comptes Microsoft et GitHub sont liées, vous pouvez utiliser ce mode d’authentification unique partout où un compte Microsoft personnel peut être utilisé, comme les sites Azure, les applications Office et Xbox. Ces comptes peuvent aussi servir de compte Microsoft pour les connexions invitées Azure Active Directory, à supposer que l’adresse e-mail correspond à celle de l’invitation.

> [!NOTE]
> En liant une identité GitHub à un compte Microsoft, vous ne communiquez aucun code d’accès à Microsoft. Quand des applications comme Azure DevOps et Visual Studio nécessitent un accès à vos dépôts de code, vous êtes invité à accorder un consentement spécifique pour cet accès. 

### <a name="frequently-asked-questions"></a>FAQ
Les questions fréquentes (FAQ) suivantes répondent aux questions que vous pouvez vous poser concernant l’utilisation des informations d’identification de votre compte GitHub pour vous connecter à des abonnements Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>Q : J’ai oublié mon mot de passe GitHub.  Comment puis-je accéder à mon compte maintenant ?
R :  Vous pouvez récupérer votre compte GitHub en accédant à [Reset your password](https://github.com/password_reset). Vous pouvez aussi récupérer votre compte Microsoft lié à GitHub en entrant l’adresse e-mail de votre compte GitHub dans le fenêtre [Récupérer votre compte](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>Q : J’ai supprimé mon compte GitHub.  Comment puis-je accéder à mon compte de service administré (MSA) Microsoft maintenant ?
R : Si vous n’avez pas d’autres informations d’identification sur votre compte MSA (comme un mot de passe, l’application Authenticator ou une clé de sécurité), vous pouvez récupérer votre compte Microsoft en utilisant l’adresse e-mail qui lui est rattachée. Pour commencer, accédez à [Récupérer votre compte](https://account.live.com/password/reset). Vous devez ajouter un mot de passe à votre compte qui déterminera ainsi la façon dont vous serez connecté par la suite. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>Q : La page de connexion ne propose pas d’option « Se connecter avec GitHub ».  Comment puis-je utiliser mes informations d’identification GitHub pour me connecter ?
R :  Tapez l’adresse e-mail de compte GitHub que vous avez choisie au moment de créer votre compte Microsoft lié à GitHub. Nous vous rechercherons et vous renverrons vers GitHub pour vous connecter. Autrement, si la page de connexion comporte un lien Options de connexion, utilisez le bouton **Se connecter avec GitHub** qui s’affiche après avoir cliqué sur ce lien. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>Q : Je ne peux pas me connecter à certaines applications et certains produits avec GitHub.  Pourquoi ?
R :  Certains produits Microsoft ne peuvent pas accéder à GitHub.com à partir de leur page de connexion. C’est notamment le cas des consoles Xbox. Ainsi, quand vous tapez l’adresse e-mail de votre compte GitHub lié, nous vous envoyons un code à cette adresse pour vérifier qu’il s’agit bien de vous. Vous vous connectez toujours au même compte, mais en employant une autre méthode de connexion. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>Q :  J’ai ajouté un mot de passe au compte Microsoft que j’ai lié à mon compte GitHub.  Cela va-t-il causer un problème ?
R :  Pas du tout. Cela ne changera pas votre mot de passe GitHub ; simplement, vous vous connecterez à votre compte Microsoft d’une autre façon. Chaque fois que vous vous connecterez en utilisant votre adresse e-mail, nous vous offrirons le choix de vous connecter avec le mot de passe de votre compte Microsoft ou d’aller sur GitHub pour vous connecter. Si vous avez besoin d’ajouter un mot de passe, nous recommandons vivement d’en utiliser un différent de celui de votre compte GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>Q : Je souhaite ajouter l’application d’authentification Authenticator au compte que j’ai créé en utilisant GitHub.  Est-ce possible ?
R :  Sans problème. Il vous suffit de télécharger l’application et de vous connecter en utilisant votre adresse e-mail. Au moment de vous connecter avec votre adresse e-mail, vous serez invité à choisir l’[application d’authentification](https://go.microsoft.com/fwlink/?linkid=2090219) ou GitHub comme informations d’identification.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Q : J’ai activé l’authentification à deux facteurs sur mes comptes GitHub et Microsoft (MSA), mais quand je me connecte à mon compte de service administré (MSA), je suis toujours invité à m’authentifier deux fois.  Pourquoi ?
R : En raison de restrictions de sécurité, Microsoft considère une connexion avec GitHub comme une vérification à facteur unique, même si vous avez activé la vérification en deux étapes. Par conséquent, vous devez vous réauthentifier pour votre compte Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Q :  Comment savoir si mes comptes Microsoft et GitHub sont liés ?
R :  Chaque fois que vous vous connectez en utilisant votre alias de compte (adresse e-mail, numéro de téléphone, nom Skype), nous vous présentons toutes les méthodes de connexion possibles pour votre compte. Si GitHub ne vous est pas proposé, c’est que vous ne l’avez pas encore configuré.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Q :  Comment dissocier mes comptes Microsoft et GitHub ? 
R :  Accédez à l’[onglet Sécurité](https://account.microsoft.com/security) sur account.microsoft.com, puis cliquez sur **Autres options de sécurité** pour dissocier votre compte GitHub. En dissociant votre compte GitHub, vous le soustrayez des méthodes de connexion et supprimez l’accès aux dépôts GitHub dans Visual Studio. Il est possible que d’autres produits Microsoft aient demandé un accès séparé à votre compte GitHub. Autrement dit, si vous supprimez l’accès ici, l’accès ne sera pas pour autant supprimé dans tous les produits. Accédez à la page [application permissions](https://github.com/settings/applications) de votre profil GitHub pour révoquer le consentement des applications listées dans cette page.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Q :  J’essaie de me connecter en utilisant mon compte GitHub, mais je suis invité à utiliser une identité Microsoft que je possède déjà.  Que se passe-t-il ?
R :  Si une adresse e-mail Azure Active Directory figure dans votre compte GitHub, cela signifie que vous avez déjà une identité Microsoft capable d’accéder à Azure et d’exécuter des pipelines d’intégration continue avec votre code GitHub. L’utilisation de ce compte est l’assurance que vos ressources et pipelines de build Azure restent dans les limites de votre organisation. Cependant, si vous effectuez un travail personnel, nous vous recommandons de placer une adresse e-mail personnelle sur votre compte GitHub, vous y aurez ainsi toujours accès. Après quoi, essayez à nouveau de vous connecter et choisissez **Utiliser une autre adresse de messagerie** quand vous êtes invité à vous connecter à votre compte professionnel ou scolaire. Cela vous permettra de créer un compte Microsoft avec cette adresse e-mail personnelle.
