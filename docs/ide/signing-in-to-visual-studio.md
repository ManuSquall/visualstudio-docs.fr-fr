---
title: Se connecter
description: Découvrez comment vous connecter à Visual Studio.
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1335ab3d8f679f00fb7f52420d378baa1f2bd905
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222992"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>connectez-vous à Visual Studio sur Windows

Bien que vous n’ayez pas à vous connecter, il existe de nombreux avantages. quand vous vous connectez, vous pouvez personnaliser, optimiser et enrichir votre expérience Visual Studio. 

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Se connecter à Visual Studio pour Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> pour utiliser des ressources configurées pour l’accès conditionnel, effectuez une mise à niveau vers Visual Studio 2019 Update 16,6 ou version ultérieure. pour plus d’informations, consultez [comment utiliser Visual Studio avec des comptes qui requièrent l’authentification multifacteur](work-with-multi-factor-authentication.md).
> l’utilisation de Visual Studio 2017 pour accéder aux ressources configurées pour l’accès conditionnel peut déclencher une dégradation de l’authentification, ce qui invite à réauthentifier plusieurs fois au sein de la même session de Visual Studio. 
> 
::: moniker-end

## <a name="benefits"></a>Avantages

Voici une liste complète de tous les avantages dont vous pouvez éventuellement bénéficier après votre connexion :

|Avantage|Description|
|---|---|
|prolonger la période d’évaluation de Visual Studio|utilisez Visual Studio Professional ou Visual Studio Enterprise **pour 90 jours supplémentaires**, au lieu d’être limité à la période d’évaluation de 30 jours. <br/>Consultez [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).|
|déverrouiller le Visual Studio (abonnement Visual Studio ou une organisation Azure DevOps)|Déverrouillez Visual Studio si vous utilisez un compte associé à un abonnement Visual Studio ou à une organisation Azure DevOps.<br/>Consultez [étendre une version d’évaluation ou mettre à jour une licence](../ide/how-to-unlock-visual-studio.md).|
|synchroniser vos paramètres de Visual Studio|Paramètres que vous personnalisez, comme les combinaisons de touches, la disposition des fenêtres et le thème de couleur, s’appliquent immédiatement lorsque vous vous connectez à Visual Studio sur n’importe quel appareil. <br/>Consultez [synchroniser les paramètres dans Visual Studio](../ide/synchronized-settings-in-visual-studio.md).|
|Se connecter automatiquement aux services|Connecter à des services, tels qu’Azure et Azure DevOps Services, dans l’IDE sans demander à nouveau les informations d’identification pour le même compte.|
|continuer à utiliser l’édition Visual Studio Community|si votre installation de Community édition vous demande une licence, connectez-vous à l’IDE pour continuer à utiliser Visual Studio Community **gratuitement**. |
|Obtient’Visual Studio Dev Essentials'|Ce programme comprend des offres logicielles gratuites, des formations, un support technique et bien plus encore. <br/>consultez [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Comment se connecter 

lorsque vous ouvrez Visual Studio pour la première fois, vous êtes invité à vous connecter et à fournir des informations d’inscription de base.

![Invite de connexion](../ide/media/vs2019_signinpopup.png)

1. Choisissez un compte Microsoft ou un compte professionnel ou scolaire qui vous représente le mieux. Si vous n’avez aucun de ces comptes, vous pouvez créer un compte Microsoft gratuitement en cliquant sur le lien situé sous le bouton se connecter. Si vous rencontrez des problèmes, consultez [Comment faire vous inscrire pour obtenir une compte Microsoft ?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Choisissez les paramètres d’interface utilisateur et le thème de couleur que vous souhaitez utiliser dans Visual Studio. Visual Studio mémorise ces paramètres et les synchronise dans tous les environnements de Visual Studio auxquels vous êtes connecté. Pour obtenir la liste des paramètres qui sont synchronisés, consultez [paramètres synchronisés](../ide/synchronized-settings-in-visual-studio.md). vous pouvez modifier les paramètres ultérieurement si vous ouvrez le menu **outils**  >  **Options** dans Visual Studio.
   Après avoir fourni les paramètres, Visual Studio démarre et vous êtes enregistré et prêt à commencer. 
   
1. Pour vérifier si vous êtes connecté, recherchez votre nom dans l'angle supérieur droit de l'environnement Visual Studio.

![Utilisateur actuellement connecté dans VS2019](../ide/media/vs2019_username.png)

si vous choisissez de ne pas vous connecter lors de la première ouverture de Visual Studio, il est facile de le faire ultérieurement. recherchez le lien de **connexion** dans le coin supérieur droit de l’environnement de Visual Studio.

![Utilisateur non connecté](../ide/media/vs2019_usernotsignedin.png)

À moins de vous déconnecter, vous êtes automatiquement connecté à Visual Studio chaque fois que vous le démarrez, et toutes les modifications apportées aux paramètres synchronisés s'appliquent automatiquement. pour vous déconnecter, cliquez sur l’icône avec le nom de votre profil dans l’angle supérieur droit de l’environnement de Visual Studio, choisissez la commande **paramètres du compte** , puis choisissez le lien **déconnexion** . Pour se connecter à nouveau, choisissez la commande **Se connecter** dans l'angle supérieur droit de l'environnement Visual Studio.

## <a name="update-your-profile"></a>Mettre à jour votre profil

1. accédez à   >  **Paramètres de compte** de fichier et choisissez le lien **gérer le profil de Visual Studio** .

1. Dans la fenêtre du navigateur, sélectionnez **Modifier le profil**, puis changez les paramètres souhaités.

1. Quand vous avez terminé, choisissez **Enregistrer les modifications**.

## <a name="troubleshooting"></a>Résolution des problèmes

Pour obtenir de l’aide, consultez la page support de l' [abonnement](https://visualstudio.microsoft.com/subscriptions/support/) .
