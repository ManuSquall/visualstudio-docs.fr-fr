---
title: Visual Studio avec un codeSpace (version préliminaire)
description: En savoir plus sur l’utilisation de l’IDE Visual Studio avec GitHub Codespaces pour le développement Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: add43a5d130d8938193774d50bb643f48ecc3f8c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104673045"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Utilisation de Visual Studio avec un codeSpace (version préliminaire)

> [!Important] 
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Nous vous encourageons à participer au [Forum](https://developercommunity.visualstudio.com/home) de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route. 

Visual Studio offre une excellente prise en charge pour le développement dans GitHub Codespaces. Vous pouvez créer et vous connecter à un codeSpace et bénéficier de toute la puissance de Visual Studio pour travailler sur vos projets sur un environnement distant hébergé. Même si votre code source et vos outils se trouvent dans un codeSpace et que votre compilation et le débogage se produisent dans le Cloud, votre expérience de développement sera aussi rapide et sans friction que si vous travailliez localement.

> [!NOTE]
> Cet article décrit spécifiquement l’utilisation de Visual Studio pour se connecter à GitHub Codespaces. Vous pouvez en savoir plus sur la connexion à un codeSpace avec d’autres clients dans la documentation [Visual Studio code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) ou [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) .

> [!NOTE]
> Si vous n’avez pas déjà installé [Visual Studio 2019 Preview](https://aka.ms/vspreview) , vous pouvez le télécharger à partir de [VisualStudio.Microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Activer la connexion à GitHub Codespaces

La connexion à GitHub Codespaces avec Visual Studio 2019 Preview n’est pas activée par défaut. vous devez d’abord activer l’option preview Features.

1. Dans la version préliminaire de Visual Studio 2019 , utilisez l'  >  élément de menu outils **options** pour ouvrir la boîte de dialogue Options.

2. Sous **environnement**, sélectionnez **fonctionnalités** en version préliminaire et cochez la fonctionnalité **se connecter à GitHub Codespaces** preview.

   ![Cochez la fonctionnalité se connecter à GitHub Codespaces preview](media/connect-to-github-codespaces-preview-feature.png)

3. Vous devrez redémarrer Visual Studio pour que la fonctionnalité soit disponible.

## <a name="create-a-codespace"></a>Créer un codeSpace

Si vous n’avez pas encore de codeSpace, vous pouvez en créer un à partir de Visual Studio.

1. Quand vous lancez Visual Studio, la fenêtre Démarrer affiche un bouton **se connecter à un codeSpace** sous « prise en main ».

   ![Fenêtre de démarrage de Visual Studio avec connexion à un codeSpace](media/visual-studio-start-window.png)

2. Sélectionnez **se connecter à un codeSpace** . vous serez invité à vous connecter à github. Vous pouvez également créer un compte GitHub, si vous n’en avez pas déjà un.

   ![Connexion de Visual Studio à GitHub](media/visual-studio-sign-in-to-github.png)

   Une fois que vous avez sélectionné **connexion à GitHub**, suivez le flux de travail de connexion GitHub en ligne.

3. Si vous n’avez jamais créé de codeSpace, vous êtes invité à en créer un.

   Sous « détails codeSpace », vous devez fournir une **URL de référentiel**. GitHub Codespaces clone le référentiel spécifié dans votre codeSpace lors de sa création.

   Vous pouvez également modifier le **type d’instance** et le **suspendre après** le délai d’attente via les listes déroulantes. Une fois que vous avez défini les détails du codeSpace, sélectionnez le bouton **créer et se connecter** .

   ![Détails de Visual Studio codeSpace](media/visual-studio-codespace-details.png)

   GitHub Codespaces va commencer à préparer le codeSpace et à ouvrir Visual Studio, une fois que le codeSpace est prêt.

   Le nom codeSpace s’affiche dans l’indicateur distant dans la barre de menus.

   ![Visual Studio connecté au référentiel eShopOnWeb codeSpace](media/visual-studio-eshoponweb-codespace.png)

4. Commencez à utiliser Visual Studio, tout comme vous le feriez localement. Solutions possibles :

   * Parcourez le code source.
   * Sélectionnez un fichier solution, puis générez la solution (**Ctrl + Maj + B**).
   * Définissez un point d’arrêt dans un fichier source et appuyez sur **F5** pour lancer l’application dans le débogueur.
   * Apportez des modifications et validez-les dans votre référentiel.   

> [!NOTE]
> À ce stade, vous ne pouvez pas créer GitHub Codespaces pour Visual Studio via le [portail GitHub Codespaces](https://github.com/codespaces). Vous ne pouvez les créer qu’à l’aide de Visual Studio.

## <a name="connect-to-a-codespace"></a>Se connecter à un codeSpace

Une fois que vous avez créé votre codeSpace, vous pouvez ouvrir votre codeSpace directement à partir de Visual Studio.

1. Quand vous lancez Visual Studio, la fenêtre Démarrer affiche un bouton **se connecter à un codeSpace** sous « prise en main ».

   ![Fenêtre de démarrage de Visual Studio avec connexion à un codeSpace](media/visual-studio-start-window.png)

   Si vous êtes déjà dans Visual Studio, vous pouvez utiliser l'   >  élément de menu **se connecter à un fichier codeSpace** .

   ![Fichier Visual Studio connexion à un élément de menu codeSpace](media/visual-studio-file-connect-to-codespace.png)

2. Sélectionnez **se connecter à un codeSpace**. Si vous ne l’avez pas déjà fait, vous serez invité à vous connecter à GitHub.

3. Vous verrez ensuite tous vos codespaces GitHub, ainsi que les détails qui s’affichent dans le volet droit.

   ![Affichage des codespaces et détails GitHub disponibles dans Visual Studio](media/visual-studio-connect-codespace.png)

   Les codespaces qui ont cloné un dépôt DevOps Azure sont uniquement visibles ici dans Visual Studio et non sur la page Codespaces de GitHub.

4. Choisissez un codeSpace et sélectionnez le bouton **se connecter** . Si le codeSpace a été suspendu, il est redémarré et Visual Studio s’ouvre connecté à ce codeSpace.

   Le nom codeSpace s’affiche dans l’indicateur distant dans la barre de menus.

   ![Visual Studio connecté au référentiel eShopOnWeb codeSpace](media/visual-studio-eshoponweb-codespace.png)

5. Commencez à utiliser Visual Studio, tout comme vous le feriez localement. Solutions possibles :

   * Parcourez le code source.
   * Sélectionnez un fichier solution, puis générez la solution (**Ctrl + Maj + B**).
   * Définissez un point d’arrêt dans un fichier source et appuyez sur **F5** pour lancer l’application dans le débogueur.
   * Apportez des modifications et validez-les dans votre référentiel.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Voir aussi

* [Qu’est-ce que GitHub Codespaces ?](codespaces-overview.md)
* [Comment personnaliser un codeSpace](customize-codespaces.md)
* [Fonctionnalités Visual Studio prises en charge](supported-features-codespaces.md)
