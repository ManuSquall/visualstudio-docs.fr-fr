---
title: Nouveautés de Visual Studio 2019
titleSuffix: ''
description: Découvrez les nouvelles fonctionnalités de Visual Studio 2019.
ms.date: 05/28/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8664606877f5393a98a78e32c6d396e1a5bcf4c1
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687688"
---
# <a name="whats-new-in-visual-studio-2019"></a>Nouveautés de Visual Studio 2019

**Mise à jour pour la [version 16,10](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Télécharger Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

Avec Visual Studio 2019, vous allez bénéficier des meilleurs outils et services pour tous les développeurs, toutes les applications et toutes les plateformes. Que vous utilisiez Visual Studio pour la première fois ou que vous l’utilisiez depuis des années, il y a beaucoup à aimer dans notre dernière version !

Voici un récapitulatif global des nouveautés et de l’ensemble :

* **[Développement](#develop)**: restez concentré et productif grâce à des performances améliorées, au nettoyage de code instantané et à de meilleurs résultats de recherche.
* **[Collaborez](#collaborate)**: Profitez de la collaboration naturelle via un flux de travail d’abord git, une modification et un débogage en temps réel et des révisions du code directement dans Visual Studio.
* **[Débogage](#debug)**: mettez en surbrillance et accédez à des valeurs spécifiques, optimisez l’utilisation de la mémoire et effectuez des instantanés automatiques de l’exécution de votre application.

Pour une liste complète de tout ce qui est nouveau dans cette version, consultez les [notes de publication](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Développer

Afficher la vidéo suivante pour en savoir plus sur la façon dont vous pouvez gagner du temps avec les nouvelles fonctionnalités. <br><br>*Longueur vidéo : 3,00 minutes*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Recherche améliorée

Anciennement appelée Lancement rapide, notre nouvelle expérience de recherche est plus rapide et plus efficace. Désormais, les résultats de la recherche apparaissent dynamiquement à mesure que vous tapez. De plus, les résultats de la recherche peuvent souvent inclure des raccourcis clavier pour les commandes, afin que vous puissiez les mémoriser pour une utilisation ultérieure.

   ![Animation de la nouvelle expérience de recherche dans Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nouvelle expérience de recherche dans Visual Studio 2019.")

La nouvelle logique de recherche approximative permet de trouver tout ce dont vous avez besoin, même en cas de fautes de frappe. Que vous recherchiez des commandes, des paramètres, de la documentation ou d’autres choses utiles, la nouvelle fonctionnalité de recherche vous permet de trouver plus facilement ce que vous cherchez.

Pour plus d’informations, consultez [utiliser la recherche Visual Studio](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Service de recherche intelligent

**Nouveauté de 16,9**: en utilisant la technologie Cloud, l’intelligence artificielle et machine learning, nous avons amélioré nos résultats de recherche. À présent, la recherche dans Visual Studio produit des résultats plus pertinents, mais elle peut également vous aider à découvrir plus facilement les fonctionnalités du produit.

Pour plus d’informations, consultez le billet de blog [intelligent Visual Studio Search service](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) .

### <a name="refactorings"></a>Refactorisations

Il existe un grand nombre de nouvelles refactorisations extrêmement utiles dans C# qui vous permettent d’organiser votre code plus facilement. Elles apparaissent comme suggestions dans l’ampoule et comprennent des actions, telles que le déplacement des membres vers une classe d’interface ou de base, l’ajustement des espaces de noms pour correspondre à la structure des dossiers, la conversion de boucles foreach en requêtes Linq et plus encore.

   ![Animation de l’expérience de refactorisations dans Visual Studio 2019](media/vs-2019/refactorings.gif "L’expérience de refactorisation dans Visual Studio 2019.")

Il vous suffit d’appeler les refactorisations en appuyant sur **Ctrl +.** et en sélectionnant l’action que vous souhaitez effectuer.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) met à profit l’intelligence artificielle (IA) pour améliorer vos efforts de développement de logiciels. Pour générer ses recommandations, IntelliCode s’entraîne sur 2 000 projets open source disponibles dans GitHub (chaque projet a plus de 100 étoiles).

![Animation d’IntelliCode dans Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode dans Visual Studio 2019.")

Voici quelques exemples illustrant comment Visual Studio IntelliCode peut améliorer votre productivité :

* Fournit des complétions de code en fonction du contexte
* Aide les développeurs à respecter les modèles et les styles de leur équipe
* Trouve des problèmes de codage difficiles à détecter
* Facilite les revues de code en attirant l’attention sur les problèmes qui sont vraiment importants

Au départ, seul C# était pris en charge dans la préversion d’IntelliCode comme extension de Visual Studio. Désormais, **nouveauté de la version 16.1**, nous avons ajouté une prise en charge « prête à l’emploi » de C# et XAML. (La prise en charge de C++ et TypeScript/JavaScript est cependant toujours en préversion.)

Et si vous utilisez C#, nous avons également ajouté la possibilité d’entraîner un modèle personnalisé sur votre propre code.

Pour plus d’informations sur IntelliCode, consultez les billets de blog [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) et [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/).

### <a name="code-cleanup"></a>Nettoyage du code

Une nouvelle commande de nettoyage de code, associée à un nouvel indicateur d’intégrité de document, vous est proposée. Vous pouvez utiliser cette nouvelle commande pour identifier, puis corriger les avertissements et les suggestions en une seule action (ou en cliquant sur un bouton).

Le nettoyage peut mettre en forme le code et appliquer les correctifs de code suggérés par les [paramètres actuels](code-styles-and-code-cleanup.md) et les [fichiers .editorconfig](create-portable-custom-editor-options.md).

   ![Capture d’écran de la nouvelle commande de nettoyage de code dans Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nouveau contrôle de nettoyage du code dans Visual Studio 2019.")

Vous pouvez aussi enregistrer des collections de correcteurs comme profil. Par exemple, si vous avez un petit ensemble de correcteurs ciblés que vous appliquez fréquemment quand vous codez, et que vous avez un autre ensemble complet de correcteurs à appliquer avant une revue du code, vous pouvez configurer des profils pour répondre à ces différentes tâches.

   ![Capture d’écran de la commande de nettoyage de code de configuration dans Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Le contrôle de nettoyage du code de configuration dans Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Rendu PMA (Per-Monitor Aware)

Si vous utilisez des moniteurs configurés avec des facteurs d’échelle d’affichage différents ou que vous vous connectez à distance à un ordinateur avec des facteurs d’échelle d’affichage différents de ceux de votre appareil principal, il est possible que Visual Studio semble flou ou qu’il ne soit pas affiché à la bonne échelle.

Avec le lancement de Visual Studio 2019, nous faisons de Visual Studio une application PMA (Per-Monitor Aware). Désormais, Visual Studio s’affiche correctement quels que soient les facteurs d’échelle d’affichage que vous utilisez.

   ![Rendu PMA (Per-Monitor Aware) dans Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Rendu par moniteur (AVM) dans Visual Studio 2019.")

Pour plus d’informations, consultez le billet de blog [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) (Une meilleure expérience sur plusieurs écrans avec Visual Studio 2019).

### <a name="test-explorer"></a>Explorateur de tests

**Nouveauté de 16,2**: nous avons mis à jour l’Explorateur de tests pour fournir une meilleure gestion des jeux de test volumineux, un filtrage plus facile, des commandes plus détectables, des vues avec onglets de sélection et des colonnes personnalisables qui vous permettent d’affiner les informations de test affichées.

   ![Capture d’écran montrant les améliorations de l’interface utilisateur dans l’Explorateur de tests](media/vs-2019/test-explorer-ui.png "Améliorations de l’interface utilisateur dans l’Explorateur de tests.")

### <a name="net-core"></a>.NET Core

**Nouveauté de 16,3**: nous avons inclus la prise en charge de .net Core 3,0. Multiplateforme, open source &mdash; et entièrement pris en charge par Microsoft.

Pour plus d’informations, consultez le billet de blog [annonçant .net Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Travailler en collaboration

Afficher la vidéo suivante pour en savoir plus sur la façon dont vous pouvez travailler en équipe pour résoudre les problèmes. <br><br>*Longueur vidéo : 4,22 minutes*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Flux de travail git-First

La nouvelle fenêtre de démarrage est l’une des choses que vous remarquez quand vous lancez Visual Studio 2019.

   ![Capture d’écran de la nouvelle fenêtre de démarrage dans Visual Studio 2019](media/vs-2019/start-window-dark.png "Nouvelle fenêtre de démarrage dans Visual Studio 2019.")

La fenêtre de démarrage vous propose plusieurs options pour vous aider à commencer à coder rapidement. Nous avons placé en premier l’option de cloner ou d’extraire du code d’un dépôt.

   ![Animation de l’expérience « Git-first » dans Visual Studio 2019](media/vs-2019/git-first.gif "L’expérience « git-First » dans Visual Studio 2019.")

La fenêtre de démarrage comprend aussi des options pour ouvrir un projet ou une solution, ouvrir un dossier local ou créer un nouveau projet.

Pour plus d’informations, consultez le billet [de blog obtenir le code suivant : comment nous avons conçu le nouveau Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Productivité git

**Nouveauté de 16,8**: git est désormais l’expérience de contrôle de version par défaut dans Visual Studio 2019. Nous avons développé l’ensemble de fonctionnalités et itéré sur ce dernier en fonction de vos commentaires au cours des deux dernières versions. La nouvelle expérience est désormais activée par défaut pour tout le monde. Dans le nouveau menu git, vous pouvez cloner, créer ou ouvrir des dépôts. Utilisez les fenêtres de l’outil git intégré pour valider et transmettre des modifications à votre code, gérer des branches, rester à jour avec vos référentiels distants et résoudre les conflits de fusion.

Pour plus d’informations, consultez la page [interface git dans Visual Studio](../version-control/git-with-visual-studio.md) .

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) est un service de développement qui vous permet de partager un code base et son contexte avec un collègue, et de bénéficier d’une collaboration bidirectionnelle instantanée directement à partir de Visual Studio. Avec Live Share, un collègue peut lire, accéder, modifier et déboguer un projet que vous avez partagé avec lui, de manière sécurisée et fluide.

Dans Visual Studio 2019, ce service est installé par défaut.

![Animation qui montre la fonctionnalité de collaboration Live Share dans Visual Studio 2019](media/vs-2019/live-share.gif "La fonctionnalité de collaboration Live Share dans Visual Studio 2019.")

Pour plus d’informations, consultez les billets de blog [Visual Studio Live Share for real-time code reviews and interactive education](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) et [Live Share now included with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/).

### <a name="integrated-code-reviews"></a>Revues de code intégrées

Nous introduisons une nouvelle extension que vous pouvez télécharger et utiliser avec Visual Studio 2019. Cette nouvelle extension vous permet de réviser, d’exécuter et même de déboguer les demandes de tirage (pull requests) de votre équipe sans quitter Visual Studio. Nous prenons en charge le code dans les dépôts GitHub et Azure DevOps.

   ![Capture d’écran de la nouvelle extension des requêtes de tirage dans Visual Studio 2019](media/vs-2019/pr-experience.png "Nouvelle extension des requêtes de tirage dans Visual Studio 2019.")

Pour plus d’informations, consultez le billet de blog [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/).

## <a name="debug"></a>Débogage

Afficher la vidéo suivante pour en savoir plus sur la façon dont vous pouvez vous concentrer sur le ciblage précis pendant le débogage. <br><br>*Longueur vidéo : 3,54 minutes*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Gains de performance

Nous avons pris les points d’arrêt de données C++, jusqu’ici exclusifs, et les avons adaptés pour les applications .NET Core.

   ![Animation qui montre les points d’arrêt de données de débogage dans Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Points d’arrêt sur les données de débogage dans Visual Studio 2019.")

Donc, si vous codez en C++ ou .NET Core, les points d’arrêt de données peuvent être une bonne alternative aux points d’arrêt ordinaires. Les points d’arrêt de données conviennent aussi très bien aux scénarios où vous devez trouver où un objet global est modifié, ajouté ou supprimé dans une liste.

Et, si vous êtes développeur C++ qui développe de grandes applications, Visual Studio 2019 crée des symboles hors processus, ce qui vous permet de déboguer ces applications sans rencontrer de problèmes liés à la mémoire.

### <a name="search-while-debugging"></a>Rechercher tout en déboguant

Il vous est sans doute déjà arrivé de rechercher une chaîne parmi un ensemble de valeurs dans la fenêtre Espion. Dans Visual Studio 2019, nous avons ajouté une fonctionnalité de recherche dans les fenêtres Espion, Variables locales et Automatique pour vous aider à trouver les objets et les valeurs qui vous intéressent.

   ![Animation qui montre la fenêtre de recherche de débogage dans Visual Studio 2019](media/vs-2019/debug-window-search.gif "La fenêtre de recherche de débogage dans Visual Studio 2019.")

Vous pouvez également mettre en forme une valeur pour changer son apparence dans les fenêtres Espion, Variables locales et Automatique. Sélectionnez (en double-cliquant sur) l’un des éléments de l’une des fenêtres et ajoutez une virgule (",") pour accéder à la liste déroulante des spécificateurs de format possibles, chacun d’entre eux incluant une description de son effet prévu.

   ![Nouvelle fenêtre Espion et fonctionnalité de mise en forme des valeurs dans Visual Studio 2019](media/search-watch-window.png "Les nouvelles fonctionnalités de Fenêtre Espion et de format dans Visual Studio 2019.")

Pour plus d’informations, consultez [améliorations dans Visual Studio 2019 : Rechercher des objets et des propriétés dans le billet de blog Windows Watch, auto et variables locales](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Débogueur de capture instantanée

Prenez une capture instantanée de l’exécution de votre application dans le cloud pour voir exactement ce qui se passe. (Cette fonctionnalité est disponible dans Visual Studio Enterprise uniquement.)

   ![Animation qui montre le Débogueur de capture instantanée dans Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "La Débogueur de capture instantanée dans Visual Studio 2019 Enterprise.")

Nous avons ajouté la prise en charge du ciblage des applications ASP.NET (Core et desktop) qui s’exécutent sur une machine virtuelle Azure. Nous avons aussi ajouté la prise en charge des applications qui s’exécutent dans Azure Kubernetes Service. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

Pour plus d’informations, voir la page [Déboguer des applications Azure ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md) et le billet de blog [Présentation du débogage avec voyage dans le temps pour Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/).

### <a name="microsoft-edge-insider-support"></a>Prise en charge de Microsoft Edge Insider

**Nouveauté de 16,2**: vous pouvez définir un point d’arrêt dans une application JavaScript et démarrer une session de débogage à l’aide du navigateur [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) . Dans ce cas, Visual Studio ouvre une nouvelle fenêtre de navigateur avec le débogage activé, que vous pouvez ensuite utiliser pour exécuter pas à pas le code JavaScript de l’application dans Visual Studio.

   ![Capture d’écran montrant le rendu de code JavaScript dans un navigateur](media/vs-2019/edge-chromium-breakpoint.png "Rendu de code JavaScript dans un navigateur.")

### <a name="pinnable-properties-tool"></a>Outil Propriétés regroupement

**Nouveauté de 16,4**: désormais, il est plus facile d’identifier les objets par leurs propriétés lors du débogage à l’aide de l’outil nouvelles propriétés regroupement. Il vous suffit de pointer le curseur sur une propriété que vous souhaitez afficher dans la fenêtre du débogueur des fenêtres espion, automatique et variables locales, de sélectionner l’icône d’épingle et de voir immédiatement les informations que vous recherchez en haut de la fenêtre.

   ![Une animation qui montre comment épingler des propriétés dans le débogueur Visual Studio à l’aide de l’outil Propriétés regroupement](media/vs-2019/debugger-pinnable-properties.gif "Épinglez les propriétés dans le débogueur Visual Studio à l’aide de l’outil Propriétés regroupement.")

Pour plus d’informations, consultez le billet de blog [Propriétés regroupement : Debug & afficher les objets gérés à votre façon](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) .

## <a name="whats-next"></a>Étapes suivantes

Nous mettons souvent à jour Visual Studio 2019 avec de nouvelles fonctionnalités susceptibles de faciliter l’expérience de développement. Pour en savoir plus sur nos dernières innovations, consultez le [blog Visual Studio](https://devblogs.microsoft.com/visualstudio/). Pour obtenir un enregistrement de ce que nous avons publié dans la version préliminaire jusqu’à ce jour, consultez les [notes de publication](/visualstudio/releases/2019/release-notes-preview/)de la version préliminaire. Pour obtenir une liste de ce que nous envisageons de publier ensuite, consultez la feuille de [route de Visual Studio](/visualstudio/productinfo/vs-roadmap).

En attendant, voici une nouvelle fonctionnalité qui est actuellement en cours d’utilisation.

- **Amélioration de l’expérience git dans Visual Studio 2019 (version préliminaire)**

   Bien que la nouvelle expérience de contrôle de version git soit désormais activée par défaut dans Visual Studio 2019 [version 16,8](/visualstudio/releases/2019/release-notes/), nous continuons à ajouter des fonctionnalités pour améliorer l’expérience dans la version préliminaire la plus récente.

   Pour plus d’informations, consultez la page [contrôle de version dans Visual Studio](/visualstudio/version-control/) .

Pour plus d’informations sur la version préliminaire de Visual Studio 2019 &mdash; et un lien de téléchargement, si vous souhaitez l’essayer, &mdash; consultez la page d' **[aperçu de Visual Studio](https://aka.ms/vspreview/)** .

> [!TIP]
> Pour en savoir plus sur la prochaine version, consultez le billet de blog **[Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)** .

## <a name="give-us-feedback"></a>Envoyer vos commentaires

Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.

* Si vous avez des suggestions sur la façon dont nous pouvons améliorer Visual Studio, utilisez l’outil [Suggérer une fonctionnalité](suggest-a-feature.md) pour nous les communiquer.

* Si vous rencontrez un problème où Visual Studio cesse de répondre, plante ou autre problème de performances, vous pouvez facilement partager les étapes de reproduction et les fichiers de prise en charge avec nous à l’aide de l’outil [signaler un problème](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Voir aussi

* [Nouveautés de la documentation de Visual Studio](whats-new-visual-studio-docs.md)
* [Notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Notes de publication de Visual Studio 2019 pour Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Nouveautés du kit de développement logiciel (SDK) Visual Studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Nouveautés de C++ dans Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Nouveautés de C# 9,0](/dotnet/csharp/whats-new/csharp-9)
* [Nouveautés de .NET 5](/dotnet/core/dotnet-five)
* [Nouveautés de .NET Framework](/dotnet/framework/whats-new/)
* [Conférence Microsoft Build](https://www.microsoft.com/build)
* [Conférence Microsoft Ignite](https://www.microsoft.com/ignite)
