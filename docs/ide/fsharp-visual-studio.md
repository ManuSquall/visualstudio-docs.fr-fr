---
title: Outils F#
description: Découvrez les fonctionnalités de Visual Studio prises en charge en F#.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f71e17eae1e728ab755d048daee2c0d156425964
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747596"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Développer avec Visual F# dans Visual Studio

Cet article contient des informations sur les fonctionnalités de Visual Studio pour le développement F#.

## <a name="install-f-support"></a>Installer la prise en charge de F#

Pour développer avec F# dans Visual Studio, installez d’abord la charge de travail **Développement .NET Desktop** si ce n’est déjà fait. Vous installez les charges de travail de Visual Studio par le biais de Visual Studio Installer, que vous pouvez ouvrir en sélectionnant **Outils** > **Obtenir des outils et fonctionnalités**.

![Charge de travail Développement .NET Desktop dans Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Fonctionnalités de projet F#

Différents modèles de projet et d’élément sont disponibles pour F# dans Visual Studio. L’illustration suivante montre certains des modèles de projet F# pour .NET Core et .NET Standard :

![Modèles de projet F# dans Visual Studio](media/fsharp-project-templates.png)

L’illustration suivante montre certains des modèles d’élément F# :

![Modèles d’élément F# dans Visual Studio](media/fsharp-item-templates.png)

Pour plus d’informations sur les modèles d’élément pour l’accès aux données, consultez [Fournisseurs de types F#](/dotnet/fsharp/tutorials/type-providers/index).

Le tableau suivant récapitule les fonctionnalités dans les propriétés de projet pour F# :

|Paramètre de projet|Pris en charge en F# ?|Notes|
|---------------|----------------|-----|
|Fichiers de ressources|Oui||
|Paramètres de référence, de débogage et de build|Oui||
|Multi-ciblage|Oui||
|Icône et manifeste|Non|Disponible par le biais des options de ligne de commande du compilateur.|
|Services client ASP.NET|Non||
|ClickOnce|Non|Utilisez un projet client dans un autre langage .NET, si c’est applicable.|
|Affectation de noms forts|Non|Disponible par le biais des options de ligne de commande du compilateur.|
|Publication et gestion de version d’assembly|Non||
|Analyse du code|Non|Les outils d’analyse de code peuvent être exécutés manuellement ou dans le cadre d’une commande post-build.|
|Sécurité (changer les niveaux de confiance)|Non||

## <a name="project-designer"></a>Concepteur de projets

Le **Concepteur de projet** se compose de plusieurs pages de propriétés de projet regroupées par fonctionnalités. Les pages disponibles pour les projets F# sont pour la plupart un sous-ensemble de celles disponibles pour d’autres langages, et sont décrites dans le tableau suivant. Des liens sont fournis vers la page C# du **Concepteur de projet** correspondante.

|Page du Concepteur de projet|Liens connexes|Description|
| - |-------------|-----------|
|Application|[Page Application, Concepteur de projet](reference/application-page-project-designer-csharp.md)|Permet de spécifier des paramètres et des propriétés au niveau de l’application, par exemple si vous créez une bibliothèque ou un fichier exécutable, quelle est la version de .NET ciblée par l’application ainsi que des informations sur l’emplacement où sont stockés les fichiers de ressources utilisés par cette application.|
|Générer|[Page Générer, Concepteur de projets](reference/build-page-project-designer-csharp.md)|Permet de contrôler comment le code est compilé.|
|Événements de build|[Page Événements de build, Concepteur de projet](reference/build-events-page-project-designer-csharp.md)|Permet de spécifier des commandes à exécuter avant ou après la compilation.|
|Débogage|[Page Déboguer, Concepteur de projet](reference/debug-page-project-designer.md)|Permet de contrôler comment l’application s’exécute pendant le débogage. Cela comprend les commandes à utiliser et l’identification du répertoire de départ de votre application, ainsi que tout mode de débogage spécial que vous souhaitez activer, tel que le code natif et SQL.|
|Package (.NET SDK uniquement)|N/A|Permet de définir les métadonnées de package NuGet lors de la publication en tant que package NuGet.|
|Chemins d'accès des références|[Gérer les références dans un projet](managing-references-in-a-project.md)|Permet de spécifier où rechercher les assemblys dont dépend le code.|
|Ressources (.NET SDK uniquement)|N/A|Permet de générer et de gérer un fichier de ressources par défaut.|

### <a name="f-specific-settings"></a>Paramètres propres à F#

Le tableau suivant récapitule les paramètres qui sont propres à F# :

|Page du Concepteur de projet|Paramètre|Description|
| - |-------|-----------|
|Générer|Générer des appels tail|Permet d’utiliser l’instruction tail MSIL (Microsoft Intermediate Language). Cela entraîne la réutilisation du frame de pile pour les fonctions récursives tail. Équivalent à l’option du compilateur `--tailcalls`.|
|Générer|Autres indicateurs|Permet de spécifier d’autres options de ligne de commande du compilateur.|

## <a name="code-and-text-editor-features"></a>Fonctionnalités d’éditeur de code et de texte

Les fonctionnalités suivantes des éditeurs de code et de texte de Visual Studio sont prises en charge en F# :

|Fonctionnalité|Description|Pris en charge en F# ?|
|-------|-----------|----------------|
|Commenter automatiquement|Permet de commenter ou de supprimer les marques de commentaire des sections de code.|Oui|
|Mettre en forme automatiquement|Remet en forme le code avec une mise en retrait et un style standard.|Non|
|Signets|Permet d’enregistrer des emplacements dans l’éditeur.|Oui|
|Changer le retrait|Met en retrait ou annule la mise en retrait des lignes sélectionnées.|Oui|
|Mise en retrait intelligente|Met en retrait et retire automatiquement la mise en retrait du curseur en fonction des règles d’étendue de F#.|Oui|
|[Rechercher et remplacer du texte](finding-and-replacing-text.md)|Permet de rechercher dans un fichier, un projet ou une solution, et éventuellement de modifier le texte.|Oui|
|Atteindre la définition pour l’API .NET|Quand le curseur est positionné sur une API .NET, montre le code généré à partir des métadonnées .NET.|Non|
|Atteindre la définition pour une API définie par l’utilisateur|Quand le curseur se trouve sur une entité de programme que vous avez définie, déplace le curseur à l’emplacement dans votre code où l’entité est définie.|Oui|
|Atteindre la ligne|Permet d’accéder à une ligne spécifique dans un fichier, par numéro de ligne.|Oui|
|Barres de navigation en haut du fichier|Permet d’accéder à des emplacements dans le code, par exemple d’après le nom de la fonction.|Oui|
|Repères de structure de bloc|Affiche des repères qui indiquent les étendues F#, dont vous pouvez afficher un aperçu en pointant dessus avec le curseur de souris.|Oui|
|[Mode Plan](outlining.md)|Permet de réduire des sections de votre code pour créer une vue plus compacte.|Oui|
|Remplacer par des tabulations|Convertit les espaces en tabulations.|Oui|
|Colorisation de type|Affiche les noms des types définis dans une couleur spécifique.|Oui|
|Recherche rapide. Voir Recherche rapide, fenêtre Rechercher et remplacer.|Permet d’effectuer une recherche dans un fichier ou un projet.|Oui|
|**Ctrl**+**clic** pour atteindre la définition|Permet d’appuyer sur **Ctrl** et de cliquer sur un symbole F# pour appeler Atteindre la définition.|Oui|
|Atteindre la définition à partir d’InfosRapides|Symboles interactifs à l’intérieur d’info-bulles qui appellent Atteindre la définition.|Oui|
|Atteindre tout|Permet une navigation globale avec correspondance approximative pour toutes les constructions F# par le biais de **Ctrl**+**T**.|Oui|
|Changement de nom inline|Renomme toutes les occurrences d’un symbole inline.|Oui|
|Rechercher toutes les références|Recherche toutes les occurrences d’un symbole dans une base de code.|Oui|
|Simplifier la correction de nom de code|Supprime les qualificateurs inutiles pour les symboles F#.|Oui|
|Supprime les corrections de code d’instructions `open` inutilisées|Supprime toutes les instructions `open` inutiles dans un document.|Oui|
|Correction de code de valeur inutilisée|Suggère de renommer un identificateur inutilisé en le remplaçant par un trait de soulignement.|Oui|

Pour obtenir des informations générales sur la modification du code dans Visual Studio et les fonctionnalités de l’éditeur de texte, consultez [Écrire du code dans l’éditeur](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>fonctions IntelliSense

Le tableau suivant récapitule les fonctionnalités IntelliSense prises en charge et non prises en charge en F# :

|Fonctionnalité|Description|Pris en charge en F# ?|
|-------|-----------|----------------|
|Implémenter automatiquement les interfaces|Génère des stubs de code pour les méthodes d’interface.|Oui|
|Extraits de code|Injecte du code à partir d’une bibliothèque de constructions de codage courantes dans les rubriques.|Non|
|Compléter le mot|Termine les mots et les noms à mesure que vous les tapez au clavier.|Oui|
|Saisie semi-automatique|Quand cette option est activée, fait en sorte que la complétion de mot sélectionne la première correspondance à mesure que vous tapez au clavier, au lieu d’attendre que vous en sélectionniez une ou que vous appuyiez sur **Ctrl**+**Espace**.|Oui|
|Offre la complétion pour les symboles dans les espaces de noms non ouverts|Avec la complétion automatique, un symbole correspondant qui se trouve dans un espace de noms non ouvert est suggéré, et la complétion avec l’instruction `open` correspondante vous est proposée.|Oui|
|Générer des éléments de code|Permet de générer du code de stub pour un large éventail de constructions.|Non|
|Liste des membres|Quand vous tapez l’opérateur d’accès au membre (.), affiche les membres d’un type.|Oui|
|Organiser les directives using/open|Organise les espaces de noms référencés par des instructions **using** en C# ou des directives **open** en F#.|Non|
|Informations sur les paramètres|Affiche des informations utiles sur les paramètres à mesure que vous tapez un appel de fonction.|Oui|
|Info express|Affiche la déclaration complète de tout identificateur dans votre code.|Oui|
|Fin d'accolade automatique|Termine automatiquement les constructions de syntaxe de type accolade F# de manière transactionnelle.|Oui|

Pour obtenir des informations générales sur IntelliSense, consultez [Utiliser IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Fonctionnalités de débogage

Le tableau suivant récapitule les fonctionnalités qui sont disponibles quand vous déboguez du code F# :

|Fonctionnalité|Description|Pris en charge en F# ?|
|-------|-----------|----------------|
|Automatique (fenêtre)|Affiche les variables automatiques ou temporaires.|Non|
|Points d’arrêt|Permet de suspendre l’exécution du code à des points spécifiques lors du débogage.|Oui|
|Points d’arrêt conditionnels|Permet de définir des points d’arrêt qui testent une condition qui détermine si l’exécution doit être suspendue.|Oui|
|Modifier & Continuer|Permet de modifier et de compiler le code à mesure que vous déboguez un programme en cours d’exécution sans arrêter et redémarrer le débogueur.|Non|
|Évaluateur d’expression|Évalue et exécute le code au moment de l’exécution.|Non, mais l’évaluateur d’expression C# peut être utilisé, bien que vous deviez utiliser la syntaxe C#.|
|Débogage d’historique|Permet d’effectuer un pas à pas détaillé du code exécuté précédemment.|Oui|
|Fenêtre Variables locales|Montre les variables et les valeurs définies localement.|Oui|
|Exécuter jusqu'au curseur|Permet d’exécuter du code jusqu’à ce que la ligne qui contient le curseur soit atteinte.|Oui|
|Pas à pas détaillé|Permet d’avancer l’exécution et d’accéder à n’importe quel appel de fonction.|Oui|
|Pas à pas principal|Permet d’avancer l’exécution dans le frame de pile actuel et de se déplacer après tout appel de fonction.|Oui|

Pour obtenir des informations générales sur le débogueur Visual Studio, consultez [Débogage dans Visual Studio](../debugger/index.md).

## <a name="additional-tools"></a>Outils supplémentaires

Le tableau suivant récapitule la prise en charge de F# dans les outils Visual Studio.

|Outil|Description|Pris en charge en F# ?|
|----|-----------|----------------|
|Hiérarchie d'appels|Affiche la structure imbriquée des appels de fonction dans votre code.|Non|
|Métrique du code|Rassemble des informations sur votre code, comme le nombre de lignes.|Non|
|Affichage de classes|Fournit une vue basée sur le type du code dans un projet.|Non|
|[Fenêtre Liste d’erreurs](reference/error-list-window.md)|Affiche une liste des erreurs dans le code.|Oui|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Permet de taper (ou copier et coller) du code F# et de l’exécuter immédiatement, indépendamment de la génération de votre projet. La fenêtre F# Interactive est une boucle REPL (Read, Evaluate, Print Loop).|Oui|
|Explorateur d'objets|Permet d’afficher les types dans un assembly.|Les types F# tels qu’ils apparaissent dans les assemblys compilés n’apparaissent pas exactement comme vous les avez créés. Vous pouvez parcourir la représentation compilée des types F#, mais vous ne pouvez pas afficher les types tels qu’ils apparaissent en F#.|
|[Fenêtre Sortie](reference/output-window.md)|Affiche la sortie de build.|Oui|
|Analyse des performances|Fournit des outils pour mesurer les performances de votre code.|Oui|
|Fenêtre Propriétés|Affiche et autorise la modification des propriétés de l’objet dans l’environnement de développement qui a le focus.|Oui|
|Explorateur de serveurs|Fournit des méthodes pour interagir avec diverses ressources de serveur.|Oui|
|Explorateur de solutions|Permet d’afficher et de gérer des projets et des fichiers.|Oui|
|Liste des tâches|Permet de gérer les éléments de travail en rapport avec votre code.|Non|
|Projets de test|Fournit des fonctionnalités qui vous aident à tester votre code.|Non|
|Boîte à outils|Affiche des onglets qui contiennent des objets déplaçables, tels que des contrôles et des sections de texte ou de code.|Oui|

## <a name="see-also"></a>Voir aussi

- [Guide F# (.NET Framework)](/dotnet/fsharp/)
- [Bien démarrer avec F# dans Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)