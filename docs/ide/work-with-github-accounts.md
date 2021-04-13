---
title: Utiliser des comptes GitHub dans Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Découvrez comment utiliser Visual Studio avec des comptes GitHub.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9f55a233cc2550cd452851edc9092b4b2f4f2411
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296363"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Utiliser des comptes GitHub dans Visual Studio

Si vous avez un compte public GitHub ou GitHub Enterprise, vous pouvez l’ajouter à votre trousseau Visual Studio. Une fois votre compte ajouté, vous pourrez tirer parti de l’intégration de la plateforme en accédant à et en créant des dépôts GitHub, directement à partir de Visual Studio.

## <a name="adding-public-github-accounts"></a>Ajout de comptes GitHub publics

Vous pouvez ajouter votre compte GitHub public si vous êtes déjà connecté à Visual Studio à l’aide d’un compte Microsoft ou d’un compte professionnel ou scolaire.

1. Sélectionnez l’icône avec vos initiales dans l’angle supérieur droit de l’environnement Visual Studio. Ensuite, sélectionnez **paramètres du compte...** pour gérer vos comptes. Vous pouvez également ouvrir la boîte de dialogue Paramètres du compte en accédant à paramètres du compte de **fichier**  >  .

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Paramètres de compte":::

2. Dans le sous-menu **tous les comptes** , sélectionnez le signe plus (+) pour ajouter un compte, puis sélectionnez **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Sélectionnez Ajouter un compte GitHub":::

3. Vous êtes redirigé vers le navigateur, où vous pouvez vous connecter avec vos informations d’identification GitHub. Une fois que vous êtes connecté, une fenêtre de réussite s’affiche dans le navigateur et vous pouvez revenir à Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Fenêtre de réussite dans le navigateur":::

4. Les deux comptes sont présents dans le sous-menu **tous les comptes** .

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Les deux comptes affichés":::

Si vous n’êtes pas déjà connecté à Visual Studio avec un autre compte, sélectionnez le lien **se connecter** dans l’angle supérieur droit de l’environnement Visual Studio. Vous pouvez également ouvrir la boîte de dialogue Paramètres du compte en accédant à paramètres du compte de **fichier**  >  . Ensuite, suivez les instructions ci-dessus pour ajouter votre compte GitHub.

![Utilisateur non connecté](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Ajout de comptes GitHub Enterprise

Par défaut, Visual Studio dispose uniquement de comptes GitHub publics activés.

1. Pour activer les comptes GitHub Enterprise, accédez à **Outils**  >  **options** et recherchez les options de **comptes** .

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menu Options des comptes":::

2. Activez ensuite la case à cocher pour **inclure les comptes de serveur GitHub Enterprise**. La prochaine fois que vous accédez à vos **paramètres de compte** et que vous essayez d’ajouter un compte GitHub, vous verrez des options pour GitHub et GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Connectez-vous avec GitHub Enterprise":::

3. Une fois que vous avez entré votre adresse de serveur GitHub Enterprise, sélectionnez **se connecter avec votre navigateur**. À partir de là, vous pouvez vous connecter en utilisant vos informations d’identification GitHub Enterprise.

## <a name="see-also"></a>Voir aussi

- [Utiliser plusieurs comptes d’utilisateur](work-with-multiple-user-accounts.md)
- [Se connecter à Visual Studio](signing-in-to-visual-studio.md)
