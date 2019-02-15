---
title: Nouveautés de Visual Studio 2019
titleSuffix: ''
description: Découvrez les nouvelles fonctionnalités de Visual Studio 2019.
ms.date: 02/08/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4667fd19f59453e9efc856aefeaaf8d43aff302d
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987416"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Nouveautés de Visual Studio 2019 Preview

**Mis à jour pour la [Préversion 2](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Télécharger la préversion](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

Visual Studio 2019 Preview inclut de nombreuses améliorations générales ainsi que de nouvelles fonctionnalités visant à optimiser la productivité des développeurs et la collaboration entre les équipes. Que vous utilisiez Visual Studio pour la première fois ou depuis des années, vous allez pouvoir tirer parti de ses fonctionnalités à tous les niveaux du cycle de vie de développement : de la création de projets simplifiée à la gestion de l’intégrité du code en passant par les flux collaboratifs en équipe et open source.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Voici un récapitulatif de ce que Visual Studio propose :

* **[Productivité des individus et des équipes](#personal-and-team-productivity)**. Productivité pour tous dans les domaines les plus importants.
* **[Prise en charge du développement moderne](#modern-development-support)**. Prise en charge des projets actifs et des solutions futures.
* **[Innovation continue](#continuous-innovation)**. Code intelligent bénéficiant d’un support cloud adapté.

> [!NOTE]
> Pour obtenir la liste complète des nouvelles fonctions et fonctionnalités de Visual Studio 2019 Preview, consultez les [notes de publication](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017). Pour un tour d’horizon des nouveautés de notre deuxième préversion, consultez le billet de blog [Visual Studio 2019 Preview 2 is now available](https://blogs.msdn.microsoft.com/visualstudio/2019/01/24/visual-studio-2019-preview-2-is-now-available/).

## <a name="personal-and-team-productivity"></a>Productivité des individus et des équipes

Il va de soi que l’amélioration des performances est la priorité numéro un de chaque nouvelle version de Visual Studio. Mais une considération tout aussi importante est l’optimisation de votre productivité. Voici comment nous pouvons vous aider.

### <a name="new-start-window"></a>Nouvelle fenêtre de démarrage

La première chose que vous remarquez quand vous lancez Visual Studio 2019 est la nouvelle fenêtre de démarrage.

   ![Nouvelle fenêtre de démarrage dans Visual Studio 2019](media/start-window.png)

Cette nouvelle fenêtre présente des options à l’aide desquelles vous pouvez cloner ou extraire du code, ouvrir un projet ou une solution, ouvrir un dossier local ou encore créer un projet. Le fait d’avoir ces options regroupées dans une boîte de dialogue simple permet aux débutants comme aux utilisateurs expérimentés de Visual Studio d’accéder rapidement au code.

Pour plus d’informations, consultez le billet de blog [Accéder au code : Comment nous avons conçu la nouvelle fenêtre de démarrage de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/).

### <a name="better-search"></a>Recherche améliorée

Anciennement appelée Lancement rapide, notre nouvelle expérience de recherche est plus rapide et plus efficace. Désormais, les résultats de la recherche apparaissent dynamiquement à mesure que vous tapez. Les résultats de la recherche incluent également les raccourcis clavier des commandes afin que vous puissiez plus facilement les mémoriser pour la suite.

   ![Nouvelle fonctionnalité de recherche dans Visual Studio 2019](media/search-feature.png)

Que vous recherchiez des commandes, des paramètres, de la documentation ou d’autres choses utiles, la nouvelle fonctionnalité de recherche vous permet de trouver plus aisément ce que vous cherchez.

### <a name="one-click-code-cleanup"></a>Nettoyage du code en un seul clic

Une nouvelle commande de nettoyage de code, associée à un nouvel indicateur d’intégrité de document, vous est proposée. Cette nouvelle commande permet d’identifier et de résoudre les avertissements et les suggestions d’un simple clic sur un bouton.

   ![Nouvelle fonctionnalité de nettoyage de code dans Visual Studio 2019](media/code-cleanup.png)

Le nettoyage peut mettre en forme le code et appliquer les correctifs de code suggérés par les [paramètres actuels](code-styles-and-quick-actions.md), les [fichiers .editorconfig](create-portable-custom-editor-options.md) ou les [analyseurs Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Améliorations du débogueur

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Effectuer une recherche dans une fenêtre Espion et mettre en forme les valeurs Espion

Il vous est sans doute déjà arrivé de rechercher une chaîne parmi un ensemble de valeurs dans la fenêtre Espion. Dans Visual Studio 2019 Preview, nous avons ajouté une fonctionnalité de recherche dans les fenêtres Espion, Variables locales et Automatique pour vous aider à trouver les objets et les valeurs qui vous intéressent.

Vous pouvez également mettre en forme une valeur pour changer son apparence dans les fenêtres Espion, Variables locales et Automatique.  Double-cliquez sur l’un des éléments dans les fenêtres et ajoutez une virgule (« , ») pour accéder à la liste déroulante des spécificateurs de format disponibles. Une description de l’effet de chaque spécificateur est fournie.

   ![Nouvelle fenêtre Espion et fonctionnalité de mise en forme des valeurs dans Visual Studio 2019](media/search-watch-window.png)

Pour plus d’informations, consultez le billet de blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://blogs.msdn.microsoft.com/visualstudio/2019/01/28/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) est un service de développement qui vous permet de partager une base de code et son contexte avec un collègue, et de bénéficier d’une collaboration bidirectionnelle instantanée directement à partir de Visual Studio. Avec Live Share, un collègue peut lire, accéder, modifier et déboguer un projet que vous avez partagé avec lui, de manière sécurisée et fluide.

Dans Visual Studio 2019 Preview, ce service est installé par défaut.

   ![Un fichier GIF animé qui présente la fonctionnalité de collaboration Live Share de Visual Studio 2019](media/live-share-collaboration.gif)

Pour plus d’informations, consultez le billet de blog [Visual Studio Live Share pour une révision du code en temps réel et une formation interactive](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/).

## <a name="modern-development-support"></a>Prise en charge du développement moderne

### <a name="manage-pull-requests-prs-from-the-ide"></a>Gérer les demandes de tirage (pull request) à partir de l’IDE

Nous introduisons une nouvelle extension que vous pouvez télécharger et utiliser avec Visual Studio 2019 Preview. Cette nouvelle extension vous permet de passer en revue, d’exécuter et même de déboguer les demandes de tirage de votre équipe sans quitter l’IDE [(environnement de développement intégré)](../get-started/visual-studio-ide.md) de Visual Studio. Nous prenons actuellement en charge le code dans Azure Repos, mais nous travaillons à étendre la fonctionnalité pour prendre en charge GitHub et améliorer l’expérience globale.

Pour démarrer, téléchargez l’extension [Pull Requests for Visual Studio](https://aka.ms/pr4vs) dans Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview"></a>Développer avec .NET Core 3 Preview

La préversion de Visual Studio 2019 prend en charge la génération d’applications [.NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.0) pour n’importe quelle plateforme. Nous allons continuer à prendre en charge et à améliorer le développement C++ multiplateforme ainsi que le développement mobile .NET pour iOS et Android avec Xamarin.

   ![Développer des applications avec .NET Core 3 Preview dans Visual Studio 2019](media/dot-net-core-three-dev.png)

Pour plus d'informations, consultez les pages suivantes :

* Notes de publication [.NET Core 3 Preview 1](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview1.md) et [.NET Core 3 Preview 2](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview2.md)
* Billets de blog [Announcing .NET Core 3 Preview 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) (Annonce de .NET Core 3 Preview 1) et [Announcing .NET Core 3 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/) (Annonce de .NET Core 3 Preview 2)

## <a name="continuous-innovation"></a>Innovation continue

### <a name="per-monitor-aware-pma-rendering"></a>Rendu PMA (Per-Monitor Aware)

Si vous utilisez des moniteurs configurés avec des facteurs d’échelle d’affichage différents ou que vous vous connectez à distance à un ordinateur avec des facteurs d’échelle d’affichage différents de ceux de votre appareil principal, il est possible que Visual Studio semble flou ou qu’il ne soit pas affiché à la bonne échelle.

Avec la publication de Visual Studio 2019 Preview, nous commençons à faire de Visual Studio une application PMA (Per-Monitor Aware). Nous posons les bases qui permettront à Visual Studio de s’afficher correctement, quel que soit les facteurs d’échelle d’affichage que vous utilisez.

   ![Rendu PMA (Per-Monitor Aware) dans Visual Studio 2019](media/per-monitor-aware-dpi-scaling.png)

Pour plus d’informations, consultez le billet de blog [Better multi-monitor experience with Visual Studio 2019](https://blogs.msdn.microsoft.com/visualstudio/2019/02/07/a-better-multi-monitor-experience-with-visual-studio-2019/) (Une meilleure expérience sur plusieurs écrans avec Visual Studio 2019).

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) est une extension qui met à profit l’intelligence artificielle (IA) pour améliorer vos efforts de développement de logiciels. Pour générer ses recommandations, IntelliCode s’entraîne sur 2 000 projets open source disponibles dans GitHub (chaque projet a plus de 100 étoiles).

Voici quelques exemples illustrant comment Visual Studio IntelliCode peut améliorer votre productivité :

* Fournit des complétions de code en fonction du contexte
* Aide les développeurs à respecter les modèles et les styles de leur équipe
* Trouve des problèmes de codage difficiles à détecter
* Facilite les revues de code en attirant l’attention sur les problèmes qui sont vraiment importants

 ![Un exemple de suggestion IntelliSense](media/intellicode-intellisense-suggestion.png)

Au départ, seul C# était pris en charge dans la préversion de l’extension IntelliCode pour Visual Studio. C++ et XAML sont désormais pris en charge dans Visual Studio.

Et si vous utilisez C#, nous avons également ajouté la possibilité d’entraîner un modèle personnalisé sur votre propre code.

Pour plus d’informations sur les mises à jour récentes, consultez le billet de blog [Visual Studio IntelliCode prend en charge plus de langages et apprend à partir de votre code](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/). Et pour plus d’informations sur l’extension et son téléchargement, consultez la page [Visual Studio IntelliCode - Préversion](https://go.microsoft.com/fwlink/?linkid=872707) sur Microsoft DevLabs.

## <a name="give-us-feedback"></a>Envoyer vos commentaires

Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.

* Si vous avez des suggestions sur la façon dont nous pouvons améliorer Visual Studio, utilisez l’outil [Fournir une suggestion](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) pour nous les faire parvenir.

* Si vous rencontrez un blocage, un plantage ou d’autres problèmes de performances, vous pouvez facilement partager avec nous les étapes de reproduction et les fichiers de prise en charge à l’aide de l’outil [Signaler un problème](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Voir aussi

* [Notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect() ; conférence en 2018](https://www.microsoft.com/connectevent)
* [Nouveautés dans Visual Studio 2017](whats-new-visual-studio-2017.md)
