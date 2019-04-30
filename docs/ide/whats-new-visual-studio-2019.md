---
title: Nouveautés de Visual Studio 2019
titleSuffix: ''
description: Découvrez les nouvelles fonctionnalités de Visual Studio 2019.
ms.date: 04/23/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 3093641ad07ad3ae0f4796c2064c3e6901ae03ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432031"
---
# <a name="whats-new-in-visual-studio-2019"></a>Nouveautés de Visual Studio 2019

**Mis à jour pour la [version 16.0](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Télécharger Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

Avec Visual Studio 2019, vous allez bénéficier des meilleurs outils et services pour tous les développeurs, toutes les applications et toutes les plateformes. Que vous utilisiez Visual Studio pour la première fois ou depuis des années, cette nouvelle version va vous plaire à de nombreux égards !

Voici un récapitulatif général des nouveautés :

* **[Développement](#develop)**  : Restez concentré et productif en profitant de performances améliorées, d’un nettoyage instantané du code et de meilleurs résultats de recherche.
* **[Collaboration](#collaborate)**  : Collaborez naturellement via un workflow « Git-first », une édition et un débogage en temps réel, et des revues de code directement dans Visual Studio.
* **[Déboguage](#debug)**  : Mettez en évidence des valeurs spécifiques pour y accéder, optimisez l’utilisation de la mémoire et prenez des captures instantanées automatiques de l’exécution de votre application.

Pour une liste complète de tout ce qui est nouveau dans cette version, consultez les [notes de publication](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Développer

Gagnez du temps avec les nouvelles fonctionnalités.
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Recherche améliorée

Anciennement appelée Lancement rapide, notre nouvelle expérience de recherche est plus rapide et plus efficace. Désormais, les résultats de la recherche apparaissent dynamiquement à mesure que vous tapez. Les résultats de recherche peuvent souvent inclure des raccourcis clavier de commandes afin que vous puissiez plus facilement les mémoriser pour la suite.

   ![Animation de la nouvelle expérience de recherche dans Visual Studio 2019](media/vs-2019/new-search-feature.gif)

La nouvelle logique de recherche approximative permet de trouver tout ce dont vous avez besoin, même en cas de fautes de frappe. Que vous recherchiez des commandes, des paramètres, de la documentation ou d’autres choses utiles, la nouvelle fonctionnalité de recherche vous permet de trouver plus facilement ce que vous cherchez.

### <a name="refactorings"></a>Refactorisations

Il existe un grand nombre de nouvelles refactorisations extrêmement utiles dans C# qui vous permettent d’organiser votre code plus facilement. Elles apparaissent comme suggestions dans l’ampoule et comprennent des actions, telles que le déplacement des membres vers une classe d’interface ou de base, l’ajustement des espaces de noms pour correspondre à la structure des dossiers, la conversion de boucles foreach en requêtes Linq et plus encore.

   ![Animation de l’expérience de refactorisations dans Visual Studio 2019](media/vs-2019/refactorings.gif)

Il vous suffit d’appeler les refactorisations en appuyant sur **Ctrl +.** et en sélectionnant l’action que vous souhaitez effectuer.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) est une extension qui met à profit l’intelligence artificielle (IA) pour améliorer vos efforts de développement de logiciels. Pour générer ses recommandations, IntelliCode s’entraîne sur 2 000 projets open source disponibles dans GitHub (chaque projet a plus de 100 étoiles).

 ![Animation d’IntelliCode dans Visual Studio 2019](media/vs-2019/IntelliCode.gif)

Voici quelques exemples illustrant comment Visual Studio IntelliCode peut améliorer votre productivité :

* Fournit des complétions de code en fonction du contexte
* Aide les développeurs à respecter les modèles et les styles de leur équipe
* Trouve des problèmes de codage difficiles à détecter
* Facilite les revues de code en attirant l’attention sur les problèmes qui sont vraiment importants

Au départ, seul C# était pris en charge dans la préversion de l’extension IntelliCode pour Visual Studio. C++ et XAML sont désormais pris en charge dans Visual Studio.

Et si vous utilisez C#, nous avons également ajouté la possibilité d’entraîner un modèle personnalisé sur votre propre code.

Pour plus d’informations sur IntelliCode, consultez le billet de blog [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/).

### <a name="code-cleanup"></a>Nettoyage du code

Une nouvelle commande de nettoyage de code, associée à un nouvel indicateur d’intégrité de document, vous est proposée. Cette nouvelle commande permet d’identifier et de résoudre les avertissements et les suggestions d’un simple clic sur un bouton.

Le nettoyage peut mettre en forme le code et appliquer les correctifs de code suggérés par les [paramètres actuels](code-styles-and-quick-actions.md) et les [fichiers .editorconfig](create-portable-custom-editor-options.md).

   ![Capture d’écran de la nouvelle commande de nettoyage de code dans Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Vous pouvez aussi enregistrer des collections de correcteurs comme profil. Par exemple, si vous avez un petit ensemble de correcteurs ciblés que vous appliquez fréquemment quand vous codez, et que vous avez un autre ensemble complet de correcteurs à appliquer avant une revue du code, vous pouvez configurer des profils pour répondre à ces différentes tâches.

   ![Capture d’écran de la nouvelle commande de nettoyage de code dans Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>Collaborer

Résolvez les problèmes en équipe.
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Workflow « cloud-first »

La nouvelle fenêtre de démarrage est l’une des choses que vous remarquez quand vous lancez Visual Studio 2019.

   ![Capture d’écran de la nouvelle fenêtre de démarrage dans Visual Studio 2019](media/vs-2019/start-window-dark.png)

La fenêtre de démarrage vous propose plusieurs options pour vous aider à commencer à coder rapidement. Nous avons placé en premier l’option de cloner ou d’extraire du code d’un dépôt.  

   ![Animation de l’expérience « Git-first » dans Visual Studio 2019](media/vs-2019/git-first.gif)

La fenêtre de démarrage comprend aussi des options pour ouvrir un projet ou une solution, ouvrir un dossier local ou créer un nouveau projet.

Pour plus d’informations, consultez le billet de blog [Accéder au code : Comment nous avons conçu la nouvelle fenêtre de démarrage de Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/).

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) est un service de développement qui vous permet de partager un code base et son contexte avec un collègue, et de bénéficier d’une collaboration bidirectionnelle instantanée directement à partir de Visual Studio. Avec Live Share, un collègue peut lire, accéder, modifier et déboguer un projet que vous avez partagé avec lui, de manière sécurisée et fluide.

Dans Visual Studio 2019, ce service est installé par défaut.

![Animation qui montre la fonctionnalité de collaboration Live Share dans Visual Studio 2019](media/vs-2019/live-share.gif)

Pour plus d’informations, consultez les billets de blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) et [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/).

### <a name="integrated-code-reviews"></a>Revues de code intégrées

Nous introduisons une nouvelle extension que vous pouvez télécharger et utiliser avec Visual Studio 2019. Cette nouvelle extension vous permet de réviser, d’exécuter et même de déboguer les demandes de tirage (pull requests) de votre équipe sans quitter Visual Studio. Nous prenons en charge le code dans les dépôts GitHub et Azure DevOps.

   ![Capture d’écran de la nouvelle fenêtre de démarrage dans Visual Studio 2019](media/vs-2019/pr-experience.png)

Pour démarrer, téléchargez l’extension [Pull Requests for Visual Studio](https://aka.ms/pr4vs) dans Visual Studio Marketplace.

## <a name="debug"></a>Débogage

Focus sur un ciblage précis.
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Gains de performance

Nous avons pris les points d’arrêt de données C++, jusqu’ici exclusifs, et les avons adaptés pour les applications .NET Core.

   ![Animation qui montre les points d’arrêt de données de débogage dans Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Donc, si vous codez en C++ ou .NET Core, les points d’arrêt de données peuvent être une bonne alternative aux points d’arrêt ordinaires. Les points d’arrêt de données conviennent aussi très bien aux scénarios où vous devez trouver où un objet global est modifié, ajouté ou supprimé dans une liste.

Et, si vous êtes développeur C++ qui développe de grandes applications, Visual Studio 2019 crée des symboles hors processus, ce qui vous permet de déboguer ces applications sans rencontrer de problèmes liés à la mémoire.

### <a name="search-while-debugging"></a>Rechercher tout en déboguant

Il vous est sans doute déjà arrivé de rechercher une chaîne parmi un ensemble de valeurs dans la fenêtre Espion. Dans Visual Studio 2019, nous avons ajouté une fonctionnalité de recherche dans les fenêtres Espion, Variables locales et Automatique pour vous aider à trouver les objets et les valeurs qui vous intéressent.

   ![Animation qui montre la fenêtre de recherche de débogage dans Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Vous pouvez également mettre en forme une valeur pour changer son apparence dans les fenêtres Espion, Variables locales et Automatique.  Double-cliquez sur l’un des éléments dans les fenêtres et ajoutez une virgule (« , ») pour accéder à la liste déroulante des spécificateurs de format disponibles. Une description de l’effet de chaque spécificateur est fournie.

   ![Nouvelle fenêtre Espion et fonctionnalité de mise en forme des valeurs dans Visual Studio 2019](media/search-watch-window.png)

Pour plus d’informations, consultez le billet de blog [Enhanced in Visual Studio 2019: Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="snapshot-debugger"></a>Débogueur de capture instantanée

Prenez une capture instantanée de l’exécution de votre application dans le cloud pour voir exactement ce qui se passe. (Cette fonctionnalité est disponible dans Visual Studio Enterprise uniquement.)

   ![Animation qui montre le Débogueur de capture instantanée dans Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Nous avons ajouté la prise en charge du ciblage des applications ASP.NET (Core et desktop) qui s’exécutent sur une machine virtuelle Azure. Nous avons aussi ajouté la prise en charge des applications qui s’exécutent dans Azure Kubernetes Service. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

Pour plus d’informations, voir la page [Déboguer des applications Azure ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md) et le billet de blog [Présentation du débogage avec voyage dans le temps pour Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/).

## <a name="whats-next"></a>Étapes suivantes

Nous mettons souvent à jour Visual Studio 2019 avec de nouvelles fonctionnalités susceptibles de faciliter l’expérience de développement. Pour en savoir plus sur nos innovations les plus récentes, consultez [Le Blog Visual Studio](https://devblogs.microsoft.com/visualstudio/). Et pour savoir ce que nous avons publié en préversion à ce jour, examinez les [Notes de publication de préversion](/visualstudio/releases/2019/release-notes-preview/).

Vous souhaitez en savoir plus sur les autres fonctionnalités prévues pour Visual Studio 2019 ? Consultez la [Feuille de route Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Envoyer vos commentaires

Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.

* Si vous avez des suggestions sur la façon dont nous pouvons améliorer Visual Studio, utilisez l’outil [Fournir une suggestion](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) pour nous les faire parvenir.

* Si vous rencontrez un blocage, un plantage ou d’autres problèmes de performances, vous pouvez facilement partager avec nous les étapes de reproduction et les fichiers de prise en charge à l’aide de l’outil [Signaler un problème](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Voir aussi

* [Annonce de Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Nouveautés du SDK Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 pour Mac est désormais disponible](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Microsoft Connect() ; conférence en 2018](https://www.microsoft.com/connectevent)
