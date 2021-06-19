---
title: Se connecter sur Windows
description: Découvrez comment vous connecter à Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b0ed679188cc0a4df9329fdd0adff4ad69667e6
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375758"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Se connecter à Visual Studio sur Windows

Bien que vous n’ayez pas à vous connecter, il existe de nombreux avantages. Quand vous vous connectez, vous pouvez personnaliser, optimiser et enrichir votre expérience Visual Studio. 

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Se connecter à Visual Studio pour Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Pour utiliser des ressources configurées pour l’accès conditionnel, effectuez une mise à niveau vers Visual Studio 2019 Update 16,6 ou version ultérieure. Pour plus d’informations, consultez [utilisation de Visual Studio avec des comptes qui requièrent l’authentification multifacteur](work-with-multi-factor-authentication.md).
> L’utilisation de Visual Studio 2017 pour accéder aux ressources configurées pour l’accès conditionnel peut déclencher une dégradation de l’authentification, ce qui invite à réauthentifier plusieurs fois au sein de la même session Visual Studio. 
> 
::: moniker-end

## <a name="benefits"></a>Avantages

Voici une liste complète de tous les avantages dont vous pouvez éventuellement bénéficier après votre connexion :


#### <a name="extend-the-visual-studio-trial-period"></a>Prolonger la période d’évaluation de Visual Studio

Vous pouvez utiliser Visual Studio Professional ou Visual Studio Enterprise pour 90 jours supplémentaires, au lieu d’être limité à la période d’évaluation de 30 jours. Pour plus d’informations, consultez [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).

#### <a name="synchronize-your-visual-studio-settings"></a>Synchroniser vos paramètres Visual Studio

Les paramètres que vous personnalisez, tels que les combinaisons de touches, la disposition des fenêtres et le thème de couleur, s’appliquent immédiatement lorsque vous vous connectez à Visual Studio sur un appareil. Consultez [synchroniser les paramètres dans Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

#### <a name="use-visual-studio-community-edition"></a>Utiliser Visual Studio Community Edition

Si l’installation de votre édition Community vous demande une licence, connectez-vous à l’IDE pour continuer à utiliser **gratuitement** Visual Studio Community. 

#### <a name="unlock-visual-studio-visual-studio-subscription-or-an-azure-devops-organization"></a>Déverrouiller Visual Studio (abonnement Visual Studio ou une organisation Azure DevOps)

Déverrouillez Visual Studio si vous utilisez un compte associé à un abonnement Visual Studio ou à une organisation Azure DevOps en suivant les étapes décrites dans [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).

#### <a name="the-visual-studio-dev-essentials-program"></a>Le programme Visual Studio Dev Essentials

Ce programme comprend des offres logicielles gratuites, des formations, un support technique et bien plus encore. Voir [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) pour obtenir de plus amples informations.

#### <a name="automatically-connect-to-services"></a>Se connecter automatiquement aux services

Connectez-vous à des services, tels qu’Azure et Azure DevOps Services, dans l’IDE sans demander à nouveau les informations d’identification pour le même compte.

## <a name="how-to-sign-in"></a>Comment se connecter 

Lorsque vous ouvrez Visual Studio pour la première fois, vous êtes invité à vous connecter et à fournir des informations d’inscription de base.

![Invite de connexion](../ide/media/vs2019_signinpopup.png)

1. Choisissez un compte Microsoft ou un compte professionnel ou scolaire qui vous représente le mieux. Si vous n’avez aucun de ces comptes, vous pouvez créer un compte Microsoft gratuitement en cliquant sur le lien situé sous le bouton se connecter. Si vous rencontrez des problèmes, consultez [Comment faire vous inscrire pour obtenir une compte Microsoft ?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Choisissez les paramètres d’interface utilisateur et le thème de couleur que vous souhaitez utiliser dans Visual Studio. Visual Studio mémorise ces paramètres et les synchronise dans tous les environnements de Visual Studio auxquels vous êtes connecté. Pour obtenir la liste des paramètres qui sont synchronisés, consultez [paramètres synchronisés](../ide/synchronized-settings-in-visual-studio.md). Vous pouvez modifier les paramètres ultérieurement si vous ouvrez le menu **Outils**  >  **options** dans Visual Studio.
   Après avoir fourni les paramètres, Visual Studio démarre et vous êtes enregistré et prêt à commencer. 
   
1. Pour vérifier si vous êtes connecté, recherchez votre nom dans l'angle supérieur droit de l'environnement Visual Studio.

![Utilisateur actuellement connecté dans VS2019](../ide/media/vs2019_username.png)

Si vous choisissez de ne pas vous connecter lorsque vous ouvrez Visual Studio pour la première fois, il est facile de le faire ultérieurement. Recherchez le lien de **connexion** dans le coin supérieur droit de l’environnement Visual Studio.

![Utilisateur non connecté](../ide/media/vs2019_usernotsignedin.png)

À moins de vous déconnecter, vous êtes automatiquement connecté à Visual Studio chaque fois que vous le démarrez, et toutes les modifications apportées aux paramètres synchronisés s'appliquent automatiquement. Pour vous déconnecter, cliquez sur l’icône avec le nom de votre profil dans l’angle supérieur droit de l’environnement Visual Studio, choisissez la commande **paramètres du compte** , puis choisissez le lien **déconnexion** . Pour se connecter à nouveau, choisissez la commande **Se connecter** dans l'angle supérieur droit de l'environnement Visual Studio.

## <a name="update-your-profile"></a>Mettre à jour votre profil

1. Accédez aux   >  **paramètres du compte** de fichier et choisissez le lien **gérer le profil Visual Studio** .

1. Dans la fenêtre du navigateur, sélectionnez **Modifier le profil**, puis changez les paramètres souhaités.

1. Quand vous avez terminé, choisissez **Enregistrer les modifications**.

## <a name="troubleshooting"></a>Dépannage

Pour obtenir de l’aide, consultez la page support de l' [abonnement](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="see-also"></a>Voir aussi

* [Prolonger une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md)
* [Utiliser des comptes GitHub dans Visual Studio](../ide/work-with-github-accounts.md)
* [Vue d’ensemble de l’IDE de Visual Studio](../get-started/visual-studio-ide.md)
