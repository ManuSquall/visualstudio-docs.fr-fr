---
title: Identités pour les abonnés Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identités pour les abonnés Visual Studio

Quand vous activez votre abonnement Visual Studio, nous lions l’identité (ou connexion) que vous avez utilisée lors de l’activation avec l’abonnement Visual Studio. Ainsi, nous pouvons vous reconnaître dans le [portail des abonnés Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), dans VSTS et dans Azure.

Dans VSTS, nous vérifions l’état de votre abonnement Visual Studio chaque fois que vous vous connectez, et nous vous octroyons des fonctionnalités automatiquement dans chaque compte dans lequel vous êtes membre. Ces fonctionnalités étant incluses comme avantages réservés aux abonnés, il est possible de vous ajouter gratuitement comme membre de n’importe quel compte VSTS lors de l’utilisation d’une identité qui est liée à votre abonnement Visual Studio.

Dans Azure, nous vérifions l’état de votre abonnement Visual Studio quand vous activez votre [crédit Azure mensuel](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) qui est un avantage réservé aux abonnés.

Dans le [portail des abonnés Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), vous pourrez peut-être ajouter une **autre identité**, en plus de celle que vous avez utilisée lors de l’activation. Aujourd’hui, nous vous autorisons à ajouter une autre identité si vous avez utilisé un compte Microsoft pour activer votre abonnement. Ainsi, vous pouvez également ajouter un compte professionnel ou scolaire (que vous utilisez pour vous connecter à Visual Studio, Office 365 ou votre réseau d’entreprise ou d’établissement scolaire), ce qui vous permet d’accéder à VSTS à la fois avec votre compte personnel et votre compte professionnel ou scolaire.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Ajout d’une autre identité à votre abonnement Visual Studio

1. Connectez-vous au [portail des abonnés Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Si vous êtes invité à choisir « compte personnel » ou « compte professionnel ou scolaire », choisissez « compte personnel » (votre compte Microsoft).
  >
  > Vous devrez parfois choisir parce que votre compte Microsoft et votre compte professionnel ou scolaire partagent la même adresse e-mail. Bien que les deux identités utilisent la même adresse e-mail, il s’agit quand même d’identités distinctes avec des autorisations, des profils et des paramètres de sécurité différents.
  >
  > Depuis le 30 mars 2018, vous ne pouvez plus créer de compte Microsoft avec une adresse e-mail qui utilise un domaine géré dans Azure Active Directory. Vous pouvez toujours vous connecter avec cette adresse e-mail en tant que compte professionnel.

2. Accédez à l’onglet **Abonnements**.

  ![Choisissez Abonnements](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. Sous **Liens connexes**, accédez à **Ajouter un autre compte**.

  ![Sous Liens connexes, accédez à Ajouter un autre compte](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Entrez votre compte professionnel ou scolaire et choisissez **Ajouter**.

  ![Entrez votre compte professionnel ou scolaire](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Utilisez votre compte professionnel ou scolaire pour vous connecter à votre compte VSTS (```https://{youraccount}.visualstudio.com```). Il peut y avoir un léger délai avant la propagation des informations. Revérifiez dans 15 minutes. 

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Q : Pourquoi VSTS ne me reconnaît-il pas comme abonné Visual Studio ?
R : VSTS doit reconnaître automatiquement votre abonnement quand vous vous connectez avec votre identité principale ou secondaire. Si ce n’est pas le cas, vous pouvez essayer les solutions suivantes :

* Vérifiez que vous disposez d’un abonnement Visual Studio actif qui [inclut VSTS en tant qu’avantage](vs-vsts.md).

* Vérifiez que vous utilisez une connexion/identité qui est l’identité principale ou secondaire de votre abonnement Visual Studio.

* Accédez au [portail des abonnés Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) au moins une fois avant de vous connecter à VSTS.

Si VSTS ne reconnaît toujours pas votre abonnement, [contactez le support technique](https://www.visualstudio.com/team-services/support/).

