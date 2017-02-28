---
title: "Glossaire MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: d014b703c491603c86fcd6a89c1dc17f35b0deae
ms.openlocfilehash: 4e0a5eca9b1d7da650c9e612076bda80b4eeda24
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-glossary"></a>Glossaire MSBuild
Ces termes sont utilisés pour décrire Microsoft Build Engine (MSBuild) et ses composants.  
  
## <a name="glossary"></a>Glossaire  
 AssemblyFoldersEx  
 Emplacement du Registre dans lequel les fournisseurs tiers stockent les chemins d’accès de chaque version de l’infrastructure qu’ils prennent en charge, où la résolution au moment du design peut rechercher des assemblys de référence.  
  
 traitement par lots  
 Répartition des éléments en différentes catégories appelées *lots*, en fonction des métadonnées d’élément, puis exécution d’une cible ou d’une tâche à la fois en utilisant chaque lot. Le traitement par lot est l’équivalent MSBuild de la construction « for loop ». Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).  
  
 étendue de génération  
 Décrit un objet MSBuild, par exemple, une propriété globale, qui est potentiellement visible pour un projet et les projets enfants créés dans une génération multiprojet.  
  
 projet enfant  
 Voir *projet, enfant*.  
  
 condition  
 De nombreux éléments MSBuild peuvent être définis de façon conditionnelle. Autrement dit, l’attribut `Condition` apparaît dans l’élément. Le contenu des éléments conditionnels est ignoré, à moins que la condition ait la valeur `true`. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).  
  
 définition, élément  
 Voir *définition d’élément*.  
  
 émettre un élément  
 Pendant la phase d’exécution d’une génération, des éléments peuvent être créés ou modifiés par des tâches dotées d’éléments `Output` enfants ayant l’attribut `ItemName`. La tâche est dite « émettre » les nouveaux éléments.  
  
 émettre une propriété  
 Pendant la phase d’exécution d’une génération, des propriétés peuvent être créées ou modifiées par des tâches dotées d’éléments `Output` enfants ayant l’attribut `PropertyName`. La tâche est dite « émettre » la nouvelle propriété.  
  
 phase d’évaluation  
 Première étape de la génération d’un projet. L’ensemble des propriétés et des éléments sont évalués dans l’ordre dans lequel ils apparaissent dans le projet. Les projets importés sont évalués à mesure qu’ils sont rencontrés dans le projet. Les cibles et les tâches ne sont pas exécutées avant la phase d’exécution, et les propriétés ou éléments déclarés ou émis sont ignorés lors de l’évaluation.  
  
 phase d’exécution  
 Seconde étape de la génération d’un projet. Les cibles sélectionnées sont générées et les tâches sont exécutées. Des propriétés et des éléments peuvent être créés ou modifiés par rapport à leurs valeurs d’évaluation.  
  
 fonction, propriété  
 Voir *fonction de propriété*.  
  
 fonction, élément  
 Voir fonction d’élément.  
  
 élément  
 Les éléments correspondent aux entrées du système de génération et sont regroupés en types d’élément basés sur leurs noms d’élément. Les éléments représentent généralement des fichiers. Comme les éléments sont nommés en fonction du type d’élément dont ils font partie, les termes *élément* et *valeur d’élément* peuvent être utilisés indifféremment. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
 définition d’élément  
 Les groupes de définitions d’élément contiennent des définitions d’élément qui ajoutent les métadonnées par défaut à tout type d’élément. À l’instar des métadonnées connues, les métadonnées par défaut sont associées à tous les éléments du type d’élément spécifié. Les métadonnées par défaut peuvent être remplacées de façon explicite dans une définition d’élément. Pour plus d’informations, consultez l’article [Item Definitions (Définitions des éléments)](../msbuild/item-definitions.md).  
  
 fonction d’élément  
 Les fonctions d’élément obtiennent des informations sur les éléments du projet. Ces fonctions simplifient l’obtention des éléments Distinct() et sont plus rapides que l’exécution d’une boucle dans les éléments. Il existe des fonctions qui permettent de manipuler les chaînes et les chemins d’accès des éléments. Pour plus d’informations, consultez l’article [Item Functions (Fonctions des éléments)](../msbuild/item-functions.md).  
  
 métadonnées d'élément  
 Voir *métadonnées, élément*.  
  
 type d’élément  
 Les types d’élément sont des listes nommées d’éléments qui peuvent être utilisés comme paramètres pour les tâches. Les tâches utilisent les valeurs d’élément pour exécuter les étapes du processus de génération. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
 métadonnées, élément  
 Les métadonnées d’élément correspondent à une collection de paires nom-valeur qui est associée à un élément. Les métadonnées fournissent des informations descriptives sur l’élément et sont facultatives, à l’exception des métadonnées connues. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
 métadonnées, connues  
 Les métadonnées connues sont des métadonnées d’élément en lecture seule qui sont initialisées à l’aide d’une valeur prédéfinie. Les métadonnées connues fournissent des informations descriptives sur un élément qui référence un fichier. Par exemple, la valeur de la métadonnée connue `FullPath` est le chemin d’accès complet du fichier référencé. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
 multi-ciblage  
 Possibilité pour un projet d’application ou d’assembly de cibler différents CLR et infrastructures à partir de MSBuild et de Visual Studio.  
  
 profile  
 Sous-ensemble de l’infrastructure totale. Permet de diminuer la quantité à télécharger sur un ordinateur.  
  
 fichier projet  
 Contient le script MSBuild qui contrôle la génération. Les fichiers projet sont généralement pourvus d’une extension de fichier se terminant par « proj », par exemple .csproj ou .vbproj. Ils peuvent importer des fichiers de propriétés et des fichiers cibles.  
  
 propriété  
 Paire clé-valeur qui permet de contrôler le processus de génération. Pour plus d’informations, consultez l’article [Propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
 propriété, environnement  
 Une propriété d’environnement est une propriété qui est initialisée automatiquement sur la valeur d’une variable d’environnement système portant le même nom. Pour plus d’informations, consultez l’article [Propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
 fichier de propriétés  
 Fichier projet qui contient principalement des groupes de propriétés et des groupes d’éléments qui guident la génération. Par convention, il est pourvu de l’extension de fichier .props. En général, les fichiers de propriétés sont importés au début des fichiers projet associés.  
  
 propriété, fonction  
 Une fonction de propriété est une propriété système ou une méthode qui peut être utilisée pour évaluer des scripts MSBuild. Les méthodes de propriété permettent de lire l’heure système, de comparer des chaînes, d’établir des correspondances avec des expressions régulières et d’effectuer d’autres actions. Pour plus d’informations, consultez l’article [Fonctions de propriétés](../msbuild/property-functions.md).  
  
 fonction de propriété, imbriquée  
 Les fonctions de propriétés peuvent être combinées pour former des fonctions plus complexes. Par exemple :  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Pour plus d’informations, consultez l’article [Fonctions de propriétés](../msbuild/property-functions.md).  
  
 propriété, globale  
 Une propriété globale est une paire clé-valeur qui permet de contrôler le processus de génération. Les propriétés globales sont définies à une invite de commandes, ou à l’aide de l’attribut `Properties` d’une [tâche MSBuild](../msbuild/msbuild-task.md), et elles ne peuvent pas être modifiées au cours de la phase d’évaluation d’une génération. Pour plus d’informations, consultez l’article [Propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
 propriété, locale  
 Une propriété locale est une paire clé-valeur qui permet de contrôler le processus de génération. Ce terme est utilisé uniquement pour distinguer une propriété qui n’est pas globale.  
  
 propriété, Registre  
 Une propriété de Registre possède une valeur qui est définie à l’aide d’une syntaxe spéciale qui lit la valeur d’une sous-clé de Registre système. Pour plus d’informations, consultez l’article [Propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
 propriété, réservée  
 Une propriété réservée est une paire clé-valeur qui permet de contrôler le processus de génération. Les propriétés réservées sont automatiquement initialisées sur les valeurs prédéfinies. Pour plus d’informations, consultez l’article [Propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
 étendue de projet  
 Décrit un objet MSBuild, par exemple, une propriété locale, qui est visible uniquement dans le fichier projet contenant et pour les projets qu’il importe.  
  
 projet, enfant  
 Un projet enfant est créé par la tâche MSBuild pendant une génération de projet. Ce nouveau projet est un enfant du projet qui contient ou importe la cible comportant la tâche MSBuild. Le projet enfant hérite des propriétés globales du projet parent, sauf si elles sont modifiées par l’attribut `Properties`.  
  
 liste de composants redistribuables  
 Liste des assemblys qui correspondent à une infrastructure donnée.  
  
 assembly de référence  
 Assembly utilisé au moment du design pour créer une application. Le code réel et les interfaces privées peuvent être supprimés d’un assembly de référence, laissant ainsi uniquement les métadonnées et les interfaces publiques.  
  
 propriété de Registre  
 Voir *propriété, Registre*.  
  
 target  
 Regroupe les tâches selon un ordre particulier et expose les sections du fichier projet comme points d’entrée du processus de génération. Pour plus d’informations, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).  
  
 cible, génération  
 Voir cible, exécution.  
  
 cible, évaluation  
 En raison de la compilation incrémentielle, les cibles doivent être analysées pour rechercher les modifications potentielles à apporter aux propriétés et aux éléments. Même si la cible est ignorée, ces modifications doivent être effectuées. Évaluer une cible signifie exécuter cette analyse et procéder à ces modifications. Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](../msbuild/incremental-builds.md) .  
  
 cible, exécution  
 Exécuter une cible signifie l’évaluer et exécuter toutes les tâches dépourvues de conditions ou dont les conditions ont la valeur true. Pendant la compilation incrémentielle, les cibles peuvent être ignorées ou exécutées, mais elles sont toujours évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».  
  
 cible, exécution  
 Une cible dont une condition a la valeur false n’est pas exécutée et n’a donc aucun effet sur la génération. Les cibles sont exécutées ou ignorées. Dans les deux cas, elles sont évaluées. Pour plus d’informations, voir l’entrée « cible, évaluation ».  
  
 cible, ignorer  
 Si la compilation incrémentielle détermine que tous les fichiers de sortie sont à jour, la cible est ignorée. En d’autres termes, la cible est évaluée, mais les tâches dans la cible ne sont pas exécutées. Pour plus d’informations, voir l’entrée « cible, évaluation ».  
  
 moniker de la version cible de .Net Framework  
 Nom qui décrit l’infrastructure (par exemple .NET Framework, Silverlight, etc.), la version et le profil (par exemple, client, serveur, etc.) que vous souhaitez cibler.  
  
 pack de ciblage  
 Liste des assemblys qui sont distribués avec une infrastructure donnée et le jeu d’assemblys de référence correspondant à cette infrastructure.  
  
 fichier de cibles  
 Fichier projet qui contient principalement des cibles et des tâches qui guident la génération. Par convention, il est pourvu de l’extension de fichier .targets. Les fichiers de cibles sont généralement importés à la fin des fichiers projet associés.  
  
 task  
 Les tâches sont des unités de code exécutable auxquelles les projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ont recours pour exécuter des opérations de génération. Par exemple, une tâche peut compiler des fichiers d’entrée ou exécuter un outil externe. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).  
  
 transformation  
 Conversion de type un-à-un d’une collection d’éléments en une autre. En plus de permettre à un projet de convertir des collections d’éléments, une transformation permet à une cible d’identifier un mappage direct entre ses entrées et sorties. Pour plus d’informations, consultez l’article [Transforms (Transformations MSBuild)](../msbuild/msbuild-transforms.md).  
  
 métadonnées connues  
 Voir *métadonnées, connues*.  
  
## <a name="see-also"></a>Voir aussi  
 [MSBuild](../msbuild/msbuild.md)
