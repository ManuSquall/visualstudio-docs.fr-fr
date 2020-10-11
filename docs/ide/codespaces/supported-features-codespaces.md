---
title: Fonctionnalités Visual Studio prises en charge (version préliminaire)
description: En savoir plus sur les fonctionnalités de l’IDE de Visual Studio disponibles lors de l’utilisation de GitHub Codespaces.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: f253ba9b7e46f809bc107aa2b3e26f635d778770
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928552"
---
# <a name="supported-visual-studio-features-preview"></a>Fonctionnalités Visual Studio prises en charge (version préliminaire)

Visual Studio fournit une expérience de développement riche lors de la connexion à un codeSpace. Vous pouvez vous procurer les outils de la boucle interne Visual Studio que vous connaissez pour modifier, déboguer, tester et mettre à niveau votre code source, ainsi que des fonctionnalités de productivité telles que les modèles de projet, la navigation dans le code riche et IntelliSense.

Dans la [version bêta publique](https://github.com/features/codespaces)actuelle de GitHub Codespaces, certaines fonctionnalités de Visual Studio peuvent ne pas être entièrement prises en charge ou peuvent être absentes initialement. Les sections suivantes décrivent ce que vous pouvez attendre de Visual Studio et de la version bêta de GitHub Codespaces et ce que vous pouvez consulter dans le futur. 

Il ne s’agit **pas d’une liste exhaustive**, mais d’expliquer les fonctionnalités générales de Visual Studio lorsqu’il est connecté à un codeSpace.

> [!NOTE]
> Si vous n’avez pas de fonctionnalité à utiliser codespaces avec Visual Studio, faites-le nous savoir en ouvrant un problème sur https://developercommunity.visualstudio.com/ . Cela nous aide à hiérarchiser les fonctionnalités les plus désirées.

> [!NOTE]
> Les fonctionnalités décrites ci-dessous sont destinées à Visual Studio et non aux deux autres clients GitHub Codespaces. Visual Studio Code et l’éditeur dans le navigateur.

## <a name="edit-and-navigation"></a>Modification et navigation

Vous devez remarquer un peu de différence de code source dans un codeSpace à mesure que vous recevez des fonctionnalités de langage intelligent telles qu’IntelliSense, la navigation dans le code, les diagnostics et les suggestions.

* Semi
* Navigation dans le code *
* Mise en forme du code avec le document de format
* Mise en surbrillance de la syntaxe
* Infos Express *
* HTML, CSS, éditeurs Razor *-prise en charge partielle.
* Éditeur JavaScript et de machine à écrire *-prise en charge partielle.

Pas encore disponible :

* IntelliSense *-certains des filtres de saisie semi-automatique/liste des membres ne sont pas disponibles. La saisie semi-automatique des types non importés et IntelliSense dans la fenêtre Espion ne sont pas encore disponibles.
* Navigation dans le code *-la plupart des commandes prises en charge. Accédez à base et recherchez dans les fichiers dont la spécification de chemin d’accès n’est pas encore prise en charge.
* Infos Express *-la colorisation dans Info Express n’est pas prise en charge.
* HTML, CSS, éditeurs Razor *-Diagnostics, saisie semi-automatique IntelliSense, info Express, mise en retrait intelligente. Il n’existe actuellement aucune prise en charge pour la coloration sémantique, les commandes de navigation, etc.
* Éditeur JavaScript et écriture automatique *-les blocs de script (par exemple, le contenu JavaScript dans les fichiers HTML et CSHTML) et la mise en surbrillance sémantique ne sont pas encore pris en charge. Problèmes connus avec les fonctionnalités d’ampoule et les Lints.
* Affichage des cibles CMake
* Éditeur de paramètres de projet CMake
* Ctrl + F7 (fichier de compilation)
* CodeLens
* Extraits de code
* IntelliCode

## <a name="application-types-and-configuration"></a>Types d’applications et configuration

La plupart des types d’applications et des configurations de projet sont pris en charge, mais vous devrez modifier votre code de projet directement sans l’aide des concepteurs visuels. Pour plus d’informations sur la configuration, voir [How to Customize a codeSpace](customize-codespaces.md).

* Modèles de projet et d’élément
* Projets .NET Core et ASP.NET Core
* Applications console C++-CMake et vcxproj pris en charge
* Applications C++ qui ciblent Linux-principalement pris en charge pour les non-GUI. Possibilité d’installer et de configurer des WSL, des fonctionnalités IntelliSense spécifiques à la plateforme et de générer.
* Modification des fichiers projet-prise en charge principalement. Certaines fonctionnalités de saisie semi-automatique, de mise en surbrillance syntaxique et de modification avancée sont manquantes.
* Comptes GitHub-peut être utilisé pour créer des ressources et se connecter à Codespaces, ainsi que pour accéder aux ressources disponibles pour le compte sur GitHub.
* Azure CLI-ne partage pas les comptes de trousseau ou d’identité Visual Studio connectés. La connexion basée sur un navigateur n’est pas prise en charge, mais vous pouvez vous authentifier à l’intérieur du terminal intégré à l’aide de : `az login --use-device-code` .

Pas encore disponible :

* Concepteurs d’interfaces utilisateur-WinForms, WPF et concepteurs de ressources
* Projets Visual Basic et F #
* .NET Framework des projets ciblés
* Projets Docker Compose
* Pages de propriétés du projet
* Options d’authentification dans les modèles de ASP.NET Core
* Applications qui nécessitent une interface utilisateur graphique pour l’installation : tout ce qui peut être installé avec le terminal est pris en charge (y compris le programme d’installation en chocolat), mais l’interface utilisateur n’est pas immédiatement disponible. L’activation de l’Live Share en mode plein écran pour accéder aux interfaces GUI est une solution de contournement actuelle. Les consoles d’administration ne sont pas accessibles. Les applications qui nécessitent un redémarrage pour l’installation ne sont pas prises en charge.
* Identités gérées pour les ressources Azure dans Visual Studio
* Ressources intranet (réseau privé)-actuellement, codespaces ne peut pas se connecter à une ressource nécessitant un VPN.
* Extensions : aucune extension n’est prise en charge lors de l’utilisation de Codespaces avec Visual Studio.

## <a name="debugging"></a>Débogage

Le débogage de boucle interne essentiel est pris en charge, notamment la définition de points d’arrêt, le pas à pas détaillé dans le code, l’inspection des variables et les fenêtres local, automatique et espion. Certaines fenêtres, personnalisations et visualiseurs supplémentaires ne sont pas pris en charge.

* Points
* Pas à pas de base
* Variables locales, automatique, regarder la prise en charge partielle de Windows *.
* Les conseils sur le serveur de symboles, le serveur source et l’importation/exportation de données sont tous partiellement pris en charge.

Pas encore disponible :

* Points d’arrêt *-les étiquettes de point d’arrêt, les points d’arrêt sur variable et le point d’arrêt défini dans la fenêtre Code machine sont en cours. L’importation et l’exportation de points d’arrêt sont partiellement prises en charge.
* Variables locales, automatique, espions Windows * : certaines fonctionnalités telles que la saisie semi-automatique des instructions dans la zone de recherche et la navigation dans la zone de recherche.
* Personnalisations de l’interface utilisateur-les propriétés regroupement et masquer les paramètres de modèle ne sont pas pris en charge.
* Visualiseurs-C++ natvis partiellement pris en charge. La fenêtre Code machine, les diagnostics visuels XAML, les visualiseurs .NET personnalisés et les visualiseurs de DataSet ne sont pas pris en charge.
* Fenêtres débogueur supplémentaires-processus Windows pris en charge de façon partielle. Fenêtre piles parallèles : la vue tâches, le hub de diagnostics et la boîte de dialogue Rechercher la source/le symbole ne sont pas pris en charge.
* Certains flux de travail du débogueur-attacher au processus, débogueur juste-à-temps (JIT), débogage de vidage, profilage et IntelliTrace ne sont pas pris en charge. C++ Uniquement mon code pas à pas est partiellement pris en charge.
* Modifier & Continuer-non pris en charge pour le code managé et le code natif.
* Les fonctionnalités de Threading, les threads Freeze et dégeler, le changement de nom du thread et l’affichage des threads dans la source ne sont pas pris en charge.
* Fonctionnalités d’étape supplémentaires : pas à pas principal dans les propriétés et les opérateurs (.NET Core) et pas à pas spécifique ne sont pris en charge. 

## <a name="features"></a>Fonctionnalités

Lorsque vous travaillez avec Visual Studio connecté à un codeSpace, vous bénéficiez des mêmes fonctionnalités d’accessibilité que lorsque vous travaillez localement.

* Contrôle de code source-prise en charge complète de git par le biais de la nouvelle [fenêtre git](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/).
* Accessibilité : il existe un problème connu avec la technologie d’assistance qui ne peut pas accéder au appcasting d’une application déboguée. Outre cette limitation, nous ne pensons pas qu’il existe d’autres problèmes de compatibilité qui n’existent pas encore dans l’expérience locale de Visual Studio. Faites-nous savoir si vous détectez des bogues en soumettant un problème à la [communauté des développeurs](https://developercommunity.visualstudio.com/).
* La publication-publier sur Azure via des actions GitHub est prise en charge.
* Services connectés : application Insights, keyvault, stockage, SQL, Redims, Cosmos, openAPI et gRPC sont partiellement pris en charge.
* Explorateur de tests *-principalement pris en charge.

Pas encore disponible :

* Explorateur de tests * : certaines fonctionnalités telles que la sélection de l’architecture par défaut, l’exécution de tests en parallèle, les sélections, etc. Problèmes connus liés au débogage d’un test unitaire, aux paramètres d’exécution et à certaines fonctionnalités d’entreprise supplémentaires. Le profilage des tests unitaires n’est pas pris en charge.
* Interface utilisateur du gestionnaire de package NuGet : la ligne de commande NuGet est prise en charge.
* Fonctionnalités de test d’entreprise : Live Unit Testing, les substituts Microsoft, la couverture du code et IntelliTest ne sont pas pris en charge.
* Scénarios de publication avancés : publication sélective, publication FTP, aperçu des modifications, barre d’outils publication rapide, etc.

## <a name="see-also"></a>Voir aussi

* [Qu’est-ce que GitHub Codespaces ?](codespaces-overview.md)
* [Utilisation de Visual Studio avec un codeSpace](use-visual-studio-with-codespaces.md)
* [Comment personnaliser un codeSpace](customize-codespaces.md)
