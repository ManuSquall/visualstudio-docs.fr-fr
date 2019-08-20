---
title: Glossaire MSBuild
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0b5feaa70a79a534af45c67e61b300feb1188bf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926355"
---
# <a name="msbuild-glossary"></a>Glossaire MSBuild

Ces termes sont utilisés pour décrire Microsoft Build Engine (MSBuild) et ses composants.

## <a name="glossary"></a>Glossaire

AssemblyFoldersEx\
Emplacement du Registre dans lequel les fournisseurs tiers stockent les chemins de chaque version du framework qu’ils prennent en charge, où la résolution au moment du design peut rechercher des assemblys de référence.

batching\
Répartition des éléments en différentes catégories appelées *lots*, en fonction des métadonnées d’élément, puis exécution d’une cible ou d’une tâche à la fois en utilisant chaque lot. Le traitement par lot est l’équivalent MSBuild de la construction « for loop ». Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).

build-scope\
Décrit un objet MSBuild, par exemple, une propriété globale, qui est potentiellement visible pour un projet et les projets enfants créés dans une génération multiprojet.

child project\
Voir *projet, enfant*.

condition\
De nombreux éléments MSBuild peuvent être définis de façon conditionnelle. Autrement dit, l’attribut `Condition` apparaît dans l’élément. Le contenu des éléments conditionnels est ignoré, à moins que la condition ait la valeur `true`. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).

definition, item\
Voir *définition d’élément*.

emit item\
Pendant la phase d’exécution d’une génération, des éléments peuvent être créés ou modifiés par des tâches dotées d’éléments `Output` enfants ayant l’attribut `ItemName`. La tâche est dite « émettre » les nouveaux éléments.

emit property\
Pendant la phase d’exécution d’une génération, des propriétés peuvent être créées ou modifiées par des tâches dotées d’éléments `Output` enfants ayant l’attribut `PropertyName`. La tâche est dite « émettre » la nouvelle propriété.

evaluation phase\
Première étape de la génération d’un projet. L’ensemble des propriétés et des éléments sont évalués dans l’ordre dans lequel ils apparaissent dans le projet. Les projets importés sont évalués à mesure qu’ils sont rencontrés dans le projet. Les cibles et les tâches ne sont pas exécutées avant la phase d’exécution, et les propriétés ou éléments déclarés ou émis sont ignorés lors de l’évaluation.

execution phase\
Seconde étape de la génération d’un projet. Les cibles sélectionnées sont générées et les tâches sont exécutées. Des propriétés et des éléments peuvent être créés ou modifiés par rapport à leurs valeurs d’évaluation.

function, property\
Voir *fonction de propriété*.

function, item\
Voir fonction d’élément.

item\
Les éléments correspondent aux entrées du système de génération et sont regroupés en types d’élément basés sur leurs noms d’élément. Les éléments représentent généralement des fichiers. Comme les éléments sont nommés en fonction du type d’élément dont ils font partie, les termes *élément* et *valeur d’élément* peuvent être utilisés indifféremment. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

item definition\
Les groupes de définitions d’élément contiennent des définitions d’élément qui ajoutent les métadonnées par défaut à tout type d’élément. À l’instar des métadonnées connues, les métadonnées par défaut sont associées à tous les éléments du type d’élément spécifié. Les métadonnées par défaut peuvent être remplacées de façon explicite dans une définition d’élément. Pour plus d’informations, consultez [Définitions d’éléments](../msbuild/item-definitions.md).

item function\
Les fonctions d’élément obtiennent des informations sur les éléments du projet. Ces fonctions simplifient l’obtention des éléments Distinct() et sont plus rapides que l’exécution d’une boucle dans les éléments. Il existe des fonctions qui permettent de manipuler les chaînes et les chemins d’accès des éléments. Pour plus d’informations, consultez [Fonctions d’élément](../msbuild/item-functions.md).

item metadata\
Voir *métadonnées, élément*.

item type\
Les types d’élément sont des listes nommées d’éléments qui peuvent être utilisés comme paramètres pour les tâches. Les tâches utilisent les valeurs d’élément pour exécuter les étapes du processus de génération. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

metadata, item\
Les métadonnées d’élément correspondent à une collection de paires nom-valeur qui est associée à un élément. Les métadonnées fournissent des informations descriptives sur l’élément et sont facultatives, à l’exception des métadonnées connues. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

metadata, well-known\
Les métadonnées connues sont des métadonnées d’élément en lecture seule qui sont initialisées à l’aide d’une valeur prédéfinie. Les métadonnées connues fournissent des informations descriptives sur un élément qui référence un fichier. Par exemple, la valeur de la métadonnée connue `FullPath` est le chemin d’accès complet du fichier référencé. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

multitargeting\
Possibilité pour un projet d’application ou d’assembly de cibler différents CLR et frameworks à partir de MSBuild et de Visual Studio.

profile\
Partie du framework entier. Permet de diminuer la quantité à télécharger sur un ordinateur.

project file\
Contient le script MSBuild qui contrôle la génération. Les fichiers projet sont généralement pourvus d’une extension de fichier se terminant par *proj*, par exemple *.csproj* ou *.vbproj*. Ils peuvent importer des fichiers de propriétés et des fichiers cibles.

property\
Paire clé-valeur qui permet de contrôler le processus de génération. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

property, environment\
Une propriété d’environnement est une propriété qui est initialisée automatiquement sur la valeur d’une variable d’environnement système portant le même nom. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

property file\
Fichier projet qui contient principalement des groupes de propriétés et des groupes d’éléments qui guident la génération. Par convention, il est pourvu de l’extension de fichier *.props*. En général, les fichiers de propriétés sont importés au début des fichiers projet associés.

property, function\
Une fonction de propriété est une propriété système ou une méthode qui peut être utilisée pour évaluer des scripts MSBuild. Les méthodes de propriété permettent de lire l’heure système, de comparer des chaînes, d’établir des correspondances avec des expressions régulières et d’effectuer d’autres actions. Pour plus d’informations, consultez [Fonctions de propriétés](../msbuild/property-functions.md).

property function, nested\
Les fonctions de propriétés peuvent être combinées pour former des fonctions plus complexes. Par exemple :

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Pour plus d’informations, consultez [Fonctions de propriétés](../msbuild/property-functions.md).

property, global\
Une propriété globale est une paire clé-valeur qui permet de contrôler le processus de génération. Les propriétés globales sont définies à une invite de commandes, ou à l’aide de l’attribut `Properties` d’une [tâche MSBuild](../msbuild/msbuild-task.md), et elles ne peuvent pas être modifiées au cours de la phase d’évaluation d’une génération. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

property, local\
Une propriété locale est une paire clé-valeur qui permet de contrôler le processus de génération. Ce terme est utilisé uniquement pour distinguer une propriété qui n’est pas globale.

property, registry\
Une propriété de Registre possède une valeur qui est définie à l’aide d’une syntaxe spéciale qui lit la valeur d’une sous-clé de Registre système. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

property, reserved\
Une propriété réservée est une paire clé-valeur qui permet de contrôler le processus de génération. Les propriétés réservées sont automatiquement initialisées sur les valeurs prédéfinies. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

project-scope\
Décrit un objet MSBuild, par exemple, une propriété locale, qui est visible uniquement dans le fichier projet contenant et pour les projets qu’il importe.

project, child\
Un projet enfant est créé par la tâche MSBuild pendant une génération de projet. Ce nouveau projet est un enfant du projet qui contient ou importe la cible comportant la tâche MSBuild. Le projet enfant hérite des propriétés globales du projet parent, sauf si elles sont modifiées par l’attribut `Properties`.

redist list\
Liste des assemblys qui correspondent à un framework donné.

reference assembly\
Assembly utilisé au moment du design pour créer une application. Le code réel et les interfaces privées peuvent être supprimés d’un assembly de référence, laissant ainsi uniquement les métadonnées et les interfaces publiques.

registry property\
Voir *propriété, Registre*.

target\
Regroupe les tâches selon un ordre particulier et expose les sections du fichier projet comme points d’entrée du processus de génération. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).

target, building\
Voir cible, exécution.

target, evaluating\
En raison de la compilation incrémentielle, les cibles doivent être analysées pour rechercher les modifications potentielles à apporter aux propriétés et aux éléments. Même si la cible est ignorée, ces modifications doivent être effectuées. Évaluer une cible signifie exécuter cette analyse et procéder à ces modifications. Pour plus d’informations, consultez [Builds incrémentielles](../msbuild/incremental-builds.md).

target, executing\
Exécuter une cible signifie l’évaluer et exécuter toutes les tâches dépourvues de conditions ou dont les conditions ont la valeur true. Pendant la compilation incrémentielle, les cibles peuvent être ignorées ou exécutées, mais elles sont toujours évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

target, running\
Une cible dont une condition a la valeur false n’est pas exécutée et n’a donc aucun effet sur la génération. Les cibles sont exécutées ou ignorées. Dans les deux cas, elles sont évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

target, skipping\
Si la compilation incrémentielle détermine que tous les fichiers de sortie sont à jour, la cible est ignorée. En d’autres termes, la cible est évaluée, mais les tâches dans la cible ne sont pas exécutées. Pour plus d’informations, voir l’entrée « cible, évaluation ».

target framework moniker\
Nom qui décrit le framework (par exemple, .NET Framework, Silverlight, etc.), la version et le profil (par exemple, client, serveur, etc.) que vous souhaitez cibler.

targeting pack\
Liste des assemblys qui sont distribués avec un framework donné et le jeu d’assemblys de référence correspondant à ce framework.

targets file\
Fichier projet qui contient principalement des cibles et des tâches qui guident la génération. Par convention, il est pourvu de l’extension de fichier *.targets*. Les fichiers de cibles sont généralement importés à la fin des fichiers projet associés.

task\
Les tâches sont des unités de code exécutable auxquelles les projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ont recours pour exécuter des opérations de génération. Par exemple, une tâche peut compiler des fichiers d’entrée ou exécuter un outil externe. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

transform\
Conversion de type un-à-un d’une collection d’éléments en une autre. En plus de permettre à un projet de convertir des collections d’éléments, une transformation permet à une cible d’identifier un mappage direct entre ses entrées et sorties. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).

well-known metadata\
Voir *métadonnées, connues*.

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)