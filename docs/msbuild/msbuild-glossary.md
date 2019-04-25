---
title: Glossaire MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f074bf7b5c7077b1c4808d7d3035be0c6366d526
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842472"
---
# <a name="msbuild-glossary"></a>Glossaire MSBuild
Ces termes sont utilisés pour décrire Microsoft Build Engine (MSBuild) et ses composants.

## <a name="glossary"></a>Glossaire
 AssemblyFoldersEx Emplacement du Registre où les fournisseurs tiers stockent les chemins de chaque version du framework qu’ils prennent en charge, et où la résolution au moment du design peut rechercher des assemblys de référence.

 traitement par lot Répartition des éléments en différentes catégories appelées *lots*, en fonction des métadonnées d’élément, puis exécution d’une cible ou d’une tâche à la fois en utilisant chaque lot. Le traitement par lot est l’équivalent MSBuild de la construction « for loop ». Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).

 étendue de la build Décrit un objet MSBuild, par exemple une propriété globale, qui est potentiellement visible par un projet et les projets enfants créés dans une build multiprojet.

 projet enfant Consultez *projet, enfant*.

 condition De nombreux éléments MSBuild peuvent être définis de façon conditionnelle. Autrement dit, l’attribut `Condition` apparaît dans l’élément. Le contenu des éléments conditionnels est ignoré, à moins que la condition ait la valeur `true`. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).

 définition, élément Consultez *définition d’élément*.

 émettre un élément Durant la phase d’exécution d’une build, des éléments peuvent être créés ou modifiés par des tâches dotées d’éléments `Output` enfants ayant l’attribut `ItemName`. La tâche est dite « émettre » les nouveaux éléments.

 émettre une propriété Durant la phase d’exécution d’une build, des propriétés peuvent être créées ou modifiées par des tâches dotées d’éléments `Output` enfants ayant l’attribut `PropertyName`. La tâche est dite « émettre » la nouvelle propriété.

 phase d’évaluation L’évaluation est la première phase d’une build de projet. L’ensemble des propriétés et des éléments sont évalués dans l’ordre dans lequel ils apparaissent dans le projet. Les projets importés sont évalués à mesure qu’ils sont rencontrés dans le projet. Les cibles et les tâches ne sont pas exécutées avant la phase d’exécution, et les propriétés ou éléments déclarés ou émis sont ignorés lors de l’évaluation.

 phase d’exécution L’exécution est la deuxième phase d’une build de projet. Les cibles sélectionnées sont générées et les tâches sont exécutées. Des propriétés et des éléments peuvent être créés ou modifiés par rapport à leurs valeurs d’évaluation.

 fonction, propriété Consultez *propriété fonction*.

 fonction, élément Consultez fonction d’élément.

 élément Les éléments correspondent aux entrées du système de build et sont regroupés en types d’élément basés sur leurs noms d’éléments. Les éléments représentent généralement des fichiers. Comme les éléments sont nommés en fonction du type d’élément dont ils font partie, les termes *élément* et *valeur d’élément* peuvent être utilisés indifféremment. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

 définition d’élément Les groupes de définitions d’élément contiennent des définitions d’élément qui ajoutent les métadonnées par défaut à tout type d’élément. À l’instar des métadonnées connues, les métadonnées par défaut sont associées à tous les éléments du type d’élément spécifié. Les métadonnées par défaut peuvent être remplacées de façon explicite dans une définition d’élément. Pour plus d’informations, consultez [Définitions d’éléments](../msbuild/item-definitions.md).

 fonction d’élément Les fonctions d’élément obtiennent des informations sur les éléments du projet. Ces fonctions simplifient l’obtention des éléments Distinct() et sont plus rapides que l’exécution d’une boucle dans les éléments. Il existe des fonctions qui permettent de manipuler les chaînes et les chemins d’accès des éléments. Pour plus d’informations, consultez [Fonctions d’élément](../msbuild/item-functions.md)

 métadonnées d’élément Consultez *métadonnées, élément*.

 type d’élément Les types d’élément sont des listes nommées d’éléments qui peuvent être utilisés en tant que paramètres pour des tâches. Les tâches utilisent les valeurs d’élément pour exécuter les étapes du processus de génération. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

 métadonnées, élément Les métadonnées d’élément correspondent à une collection de paires nom-valeur, qui est associée à un élément. Les métadonnées fournissent des informations descriptives sur l’élément et sont facultatives, à l’exception des métadonnées connues. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

 métadonnées, connues Les métadonnées connues sont des métadonnées d’élément en lecture seule qui sont initialisées à l’aide d’une valeur prédéfinie. Les métadonnées connues fournissent des informations descriptives sur un élément qui référence un fichier. Par exemple, la valeur de la métadonnée connue `FullPath` est le chemin d’accès complet du fichier référencé. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

 multiciblage Possibilité pour un projet d’application ou d’assembly de cibler différents CLR et frameworks à partir de MSBuild et de Visual Studio.

 profil Partie du framework entier. Permet de diminuer la quantité à télécharger sur un ordinateur.

 fichier projet Un fichier projet contient le script MSBuild qui contrôle la build. Les fichiers projet sont généralement pourvus d’une extension de fichier se terminant par *proj*, par exemple *.csproj* ou *.vbproj*. Ils peuvent importer des fichiers de propriétés et des fichiers cibles.

 propriété Une propriété est une paire clé-valeur utilisée pour contrôler le processus de génération. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

 propriété, environnement Une propriété d’environnement est une propriété qui est initialisée automatiquement avec la valeur d’une variable d’environnement système portant le même nom. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

 fichier de propriétés Fichier projet qui contient principalement des groupes de propriétés et des groupes d’éléments qui guident la build. Par convention, il est pourvu de l’extension de fichier *.props*. En général, les fichiers de propriétés sont importés au début des fichiers projet associés.

 propriété, fonction Une fonction de propriété est une propriété système ou une méthode qui permet d’évaluer des scripts MSBuild. Les méthodes de propriété permettent de lire l’heure système, de comparer des chaînes, d’établir des correspondances avec des expressions régulières et d’effectuer d’autres actions. Pour plus d’informations, consultez [Fonctions de propriétés](../msbuild/property-functions.md).

 fonction de propriété, imbriquée Les fonctions de propriétés peuvent être combinées pour former des fonctions plus complexes. Par exemple :

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Pour plus d’informations, consultez [Fonctions de propriétés](../msbuild/property-functions.md).

 propriété, globale Une propriété globale est une paire clé-valeur utilisée pour contrôler le processus de génération. Les propriétés globales sont définies à une invite de commandes, ou à l’aide de l’attribut `Properties` d’une [tâche MSBuild](../msbuild/msbuild-task.md), et elles ne peuvent pas être modifiées au cours de la phase d’évaluation d’une génération. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

 propriété, locale Une propriété locale est une paire clé-valeur utilisée pour contrôler le processus de génération. Ce terme est utilisé uniquement pour distinguer une propriété qui n’est pas globale.

 propriété, Registre Une propriété de Registre a une valeur définie à l’aide d’une syntaxe spéciale qui lit la valeur d’une sous-clé du Registre système. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

 propriété, réservée Une propriété réservée est une paire clé-valeur utilisée pour contrôler le processus de génération. Les propriétés réservées sont automatiquement initialisées sur les valeurs prédéfinies. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

 étendue du projet Décrit un objet MSBuild, par exemple une propriété locale, visible uniquement dans le fichier projet conteneur et par les projets importés.

 projet, enfant Un projet enfant est créé par la tâche MSBuild pendant une build de projet. Ce nouveau projet est un enfant du projet qui contient ou importe la cible comportant la tâche MSBuild. Le projet enfant hérite des propriétés globales du projet parent, sauf si elles sont modifiées par l’attribut `Properties`.

 liste de redistribution Liste des assemblys qui correspondent à un framework donné.

 assembly de référence Assembly utilisé au moment du design pour créer une application. Le code réel et les interfaces privées peuvent être supprimés d’un assembly de référence, laissant ainsi uniquement les métadonnées et les interfaces publiques.

 propriété de registre Consultez *propriété, registre*.

 cible Regroupe les tâches selon un ordre particulier et expose les sections du fichier projet en tant que points d’entrée du processus de génération. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).

 cible, génération Consultez cible, exécution.

 cible, évaluation En raison de la compilation incrémentielle, les cibles doivent être analysées pour permettre la recherche de changements potentiels apportés aux propriétés et aux éléments. Même si la cible est ignorée, ces modifications doivent être effectuées. Évaluer une cible signifie exécuter cette analyse et procéder à ces modifications. Pour plus d’informations, consultez [Builds incrémentielles](../msbuild/incremental-builds.md).

 cible, exécution Exécuter une cible signifie l’évaluer et exécuter toutes les tâches dépourvues de conditions ou dont les conditions ont la valeur true. Pendant la compilation incrémentielle, les cibles peuvent être ignorées ou exécutées, mais elles sont toujours évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

 cible exécution Une cible dont une condition a la valeur false n’est pas exécutée et n’a donc aucun effet sur la build. Les cibles sont exécutées ou ignorées. Dans les deux cas, elles sont évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

 cible, ignorée Si la compilation incrémentielle détermine que tous les fichiers de sortie sont à jour, la cible est ignorée. En d’autres termes, la cible est évaluée, mais les tâches qu’elle contient ne sont pas exécutées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

 moniker de framework cible Nom qui décrit le framework (par exemple le .NET Framework, Silverlight, etc.), la version et le profil (par exemple client, serveur, etc.) que vous souhaitez cibler.

 pack de ciblage Liste des assemblys distribués avec un framework donné et jeu d’assemblys de référence correspondant à ce framework.

 fichier de cibles Fichier projet qui contient principalement des cibles et des tâches qui guident la build. Par convention, il est pourvu de l’extension de fichier *.targets*. Les fichiers de cibles sont généralement importés à la fin des fichiers projet associés.

 tâche Les tâches sont des unités de code exécutable que les projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utilisent pour effectuer des opérations de build. Par exemple, une tâche peut compiler des fichiers d'entrée ou exécuter un outil externe. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

 transformation Il s’agit d’une conversion de type un-à-un d’une collection d’éléments vers une autre. En plus de permettre à un projet de convertir des collections d’éléments, une transformation permet à une cible d’identifier un mappage direct entre ses entrées et sorties. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).

 métadonnées connues Consultez *métadonnées, connues*.

## <a name="see-also"></a>Voir aussi
- [MSBuild](../msbuild/msbuild.md)