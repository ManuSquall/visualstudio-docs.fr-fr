---
title: Se connecter à Visual Studio
description: Découvrez comment vous connecter à Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87c0ad7517bb01aa68d98e0502e34af7c767e962
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683988"
---
# <a name="sign-in-to-visual-studio"></a>Se connecter à Visual Studio

Vous pouvez personnaliser et optimiser votre expérience de développement dans Visual Studio en vous connectant à votre compte de personnalisation.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Se connecter à Visual Studio pour Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! Avertissement] l’utilisation de Visual Studio 2017 pour accéder aux ressources configurées pour l’accès conditionnel peut déclencher une dégradation de l’authentification, ce qui invite à réauthentifier plusieurs fois au sein de la même session Visual Studio. 
> Pour utiliser des ressources configurées pour l’accès conditionnel, effectuez une mise à niveau vers Visual Studio 2019 Update 16,6 ou version ultérieure. Pour plus d’informations, consultez [utilisation de Visual Studio avec des comptes qui requièrent l’authentification multifacteur](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Pourquoi dois-je me connecter à Visual Studio ?

Quand vous vous connectez, vous bénéficiez de nombreux avantages supplémentaires dans Visual Studio. Par exemple, une fois que vous êtes connecté, vous pouvez [synchroniser vos paramètres](synchronized-settings-in-visual-studio.md) sur plusieurs appareils, étendre une version d’évaluation et vous connecter automatiquement à un service Azure, pour n’en nommer que quelques-uns.

Voici une liste complète de tous les avantages dont vous pouvez éventuellement bénéficier après votre connexion :
- **Prolongez la période d’évaluation de Visual Studio** : vous pouvez utiliser Visual Studio Professional ou Visual Studio Enterprise pendant 90 jours supplémentaires, au lieu de vous limiter à la période d’évaluation de 30 jours. Pour plus d’informations, consultez [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).

- **Continuer à utiliser l’édition Visual Studio Community** : si l’installation de votre édition Community vous demande une licence, connectez-vous à l’IDE pour continuer à utiliser Visual Studio Community **gratuitement**. 

- **Déverrouillez Visual Studio si vous utilisez un compte associé à un abonnement Visual Studio ou à une organisation Azure DevOps**. Pour obtenir des instructions détaillées, consultez [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).

- **Accédez à Visual Studio Dev Essentials** : ce programme inclut des logiciels gratuits, des formations, un support technique, et plus encore. Voir [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) pour obtenir de plus amples informations.

- **Synchronisez vos paramètres Visual Studio** : les paramètres que vous personnalisez, comme les combinaisons de touches, la disposition des fenêtres et le thème de couleur, s’appliquent immédiatement quand vous vous connectez à Visual Studio sur un appareil. Consultez [synchroniser les paramètres dans Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Connectez-vous automatiquement à des services comme Azure et Azure DevOps Services** dans l’IDE sans avoir à fournir à nouveau les informations d’identification pour le même compte.

## <a name="how-to-sign-in-to-visual-studio"></a>Comment se connecter à Visual Studio ?

Lorsque vous ouvrez Visual Studio pour la première fois, vous êtes invité à vous connecter et à fournir des informations d’inscription de base.

![Invite de connexion](../ide/media/vs2019_signinpopup.png)

Vous devez choisir un compte Microsoft ou bien un compte professionnel ou scolaire qui vous représente le mieux. Si vous n’avez aucun de ces comptes, vous pouvez créer un compte Microsoft gratuitement en cliquant sur le lien situé sous le bouton se connecter. Si vous rencontrez des problèmes, consultez [Comment faire vous inscrire pour obtenir une compte Microsoft ?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Choisissez ensuite les paramètres d'interface utilisateur et le thème de couleur que vous souhaitez utiliser dans Visual Studio. Visual Studio mémorise ces paramètres et les synchronise dans tous les environnements de Visual Studio auxquels vous êtes connecté. Pour obtenir la liste des paramètres qui sont synchronisés, consultez [paramètres synchronisés](../ide/synchronized-settings-in-visual-studio.md). Vous pouvez modifier les paramètres ultérieurement si vous ouvrez le menu **Outils**  >  **options** dans Visual Studio.

Après avoir fourni les paramètres, Visual Studio démarre et vous êtes enregistré et prêt à commencer. Pour vérifier si vous êtes connecté, recherchez votre nom dans l'angle supérieur droit de l'environnement Visual Studio.

![Utilisateur actuellement connecté dans VS2019](../ide/media/vs2019_username.png)

Si vous choisissez de ne pas vous connecter lorsque vous ouvrez Visual Studio pour la première fois, il est facile de le faire ultérieurement. Recherchez le lien de **connexion** dans le coin supérieur droit de l’environnement Visual Studio.

![Utilisateur non connecté](../ide/media/vs2019_usernotsignedin.png)

À moins de vous déconnecter, vous êtes automatiquement connecté à Visual Studio chaque fois que vous le démarrez, et toutes les modifications apportées aux paramètres synchronisés s'appliquent automatiquement. Pour vous déconnecter, cliquez sur l’icône avec le nom de votre profil dans l’angle supérieur droit de l’environnement Visual Studio, choisissez la commande **paramètres du compte** , puis choisissez le lien **déconnexion** . Pour se connecter à nouveau, choisissez la commande **Se connecter** dans l'angle supérieur droit de l'environnement Visual Studio.

## <a name="to-change-your-profile-information"></a>Pour modifier vos informations de profil

1. Accédez aux   >  **paramètres du compte** de fichier et choisissez le lien **gérer le profil Visual Studio** .

1. Dans la fenêtre du navigateur, sélectionnez **Modifier le profil**, puis changez les paramètres souhaités.

1. Quand vous avez terminé, choisissez **Enregistrer les modifications**.

## <a name="troubleshooting"></a>Dépannage

Si vous rencontrez des problèmes lors de la connexion, veuillez consulter la page de support de l' [abonnement](https://visualstudio.microsoft.com/subscriptions/support/) pour obtenir de l’aide.

## <a name="see-also"></a>Voir aussi

* [Prolonger une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md)
* [Utiliser des comptes GitHub dans Visual Studio](../ide/work-with-github-accounts.md)
* [Vue d’ensemble de l’IDE de Visual Studio](../get-started/visual-studio-ide.md)
* [Se connecter (Visual Studio pour Mac)](/visualstudio/mac/signing-in)
* [Activation (Visual Studio pour Mac)](/visualstudio/mac/activation)
