---
title: MSBuild | Microsoft Docs
description: Découvrez comment la plateforme Microsoft Build Engine (MSBuild) fournit un fichier projet avec un schéma XML pour contrôler les builds.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848277"
---
# <a name="msbuild"></a>MSBuild

Le Microsoft Build Engine est une plateforme de création d’applications. Ce moteur, également appelé MSBuild, fournit un schéma XML pour un fichier projet qui contrôle la manière dont la plateforme de génération traite et génère les logiciels. Visual Studio utilise MSBuild, mais MSBuild ne dépend pas de Visual Studio. En appelant *msbuild.exe* sur votre fichier projet ou solution, vous pouvez orchestrer et générer des produits dans les environnements où Visual Studio n’est pas installé.

 Visual Studio utilise MSBuild pour charger et générer des projets managés. Les fichiers projet de Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* et autres) contiennent du code XML MSBuild qui s’exécute lors de la génération d’un projet avec l’environnement IDE. Les projets Visual Studio importent tous les paramètres et processus de génération nécessaires pour effectuer le travail de développement classique, mais vous pouvez les développer ou les modifier à partir de Visual Studio ou en utilisant un éditeur XML.

 Pour plus d’informations sur MSBuild pour C++, consultez [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Les exemples suivants illustrent les cas où vous pouvez exécuter des builds en appelant MSBuild à partir de la ligne de commande au lieu de l’IDE de Visual Studio.

- Visual Studio n'est pas installé. ([Téléchargez MSBuild sans Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Vous souhaitez utiliser la version 64 bits de MSBuild. Cette version MSBuild est généralement inutile, mais elle permet à MSBuild d'accéder à plus de mémoire.

- Vous souhaitez exécuter une build dans plusieurs processus. Toutefois, vous pouvez utiliser l'IDE pour obtenir le même résultat sur les projets dans C++ et C#.

- Vous souhaitez modifier le système de génération. Par exemple, vous pouvez souhaiter effectuer les actions suivantes :

  - Prétraitez les fichiers avant qu'ils n'atteignent le compilateur.

  - Copiez les sorties de génération à un autre emplacement.

  - Créez des fichiers compressés à partir des sorties de génération.

  - Procédez à une étape de post-traitement. Par exemple, vous pouvez souhaiter horodater un assembly avec une version différente.

Vous pouvez écrire du code dans l'IDE de Visual Studio, mais les générations s'exécutent à l'aide de MSBuild. Vous pouvez également générer du code dans l’IDE sur un ordinateur de développement, mais exécuter MSBuild à partir de la ligne de commande pour générer le code intégré à partir de plusieurs développeurs. Vous pouvez également utiliser l' [interface de ligne de commande (CLI) .net Core](/dotnet/core/tools/), qui utilise MSBuild, pour générer des projets .net core.

> [!NOTE]
> Vous pouvez utiliser Azure Pipelines pour compiler, tester et déployer automatiquement votre application. Votre système de génération peut automatiquement exécuter des générations lorsque les développeurs archivent du code (par exemple, dans le cadre d'une stratégie continue d'intégration) ou selon une planification (par exemple, une build nocturne de test de vérification de build). Azure Pipelines compile votre code à l’aide de MSBuild. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Cet article fournit une vue d’ensemble de MSBuild. Pour un didacticiel d’introduction, consultez la [Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Utiliser MSBuild dans une invite de commandes

 Pour exécuter MSBuild à partir d’une invite de commandes, transmettez un fichier projet à *MSBuild.exe*, ainsi que les options de ligne de commande appropriées. Les options de ligne de commande vous permettent de définir des propriétés, d'exécuter des cibles spécifiques et de définir d'autres options qui contrôlent le processus de génération. Par exemple, la syntaxe de ligne de commande suivante permet de générer le fichier *MyProj.proj* avec la propriété `Configuration` définie sur `Debug`.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Pour plus d’informations sur les options de ligne de commande MSBuild, consultez [référence de la ligne de commande](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Avant de télécharger un projet, déterminez la crédibilité du code.

## <a name="project-file"></a>Fichier projet

 MSBuild utilise un format de fichier projet XML qui est simple et extensible. Le format de fichier projet MSBuild permet aux développeurs de décrire les éléments qui doivent être générés, ainsi que la façon dont ils doivent être générés pour différents systèmes d’exploitation et configurations. De plus, le format de fichier projet permet aux développeurs de créer des règles de génération réutilisables qui peuvent être réparties en fichiers distincts, de telle sorte que les builds puissent être exécutées de façon cohérente sur différents projets du produit.

 Les sections suivantes décrivent certains des éléments de base du format de fichier projet MSBuild. Pour obtenir un didacticiel sur la création d’un fichier projet de base, consultez [procédure pas à pas : création d’un fichier projet MSBuild en partant de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Propriétés

 Les propriétés sont des paires clé/valeur qui peuvent être utilisées pour configurer les générations. Les propriétés sont déclarées en créant un élément portant le nom de la propriété comme enfant d’un élément [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Par exemple, le code suivant crée une propriété nommée `BuildDir` avec la valeur `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Vous pouvez définir une propriété conditionnellement en plaçant un attribut `Condition` dans l'élément. Le contenu des éléments conditionnels est ignoré, à moins que la condition ait la valeur `true`. Dans l'exemple suivant, l'élément `Configuration` est défini s'il n'a pas encore été défini.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Les propriétés peuvent être référencées dans tout le fichier projet à l’aide de la syntaxe $ ( \<PropertyName> ). Par exemple, vous pouvez référencer les propriétés dans les exemples précédents en utilisant `$(BuildDir)` et `$(Configuration)`.

 Pour plus d’informations sur les propriétés, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Contenus

 Les éléments sont des entrées du système de génération qui représentent généralement des fichiers. Les éléments sont regroupés en types d’éléments en fonction des noms d’élément définis par l’utilisateur. Ces types d’éléments peuvent être utilisés comme paramètres des tâches, lesquelles utilisent les éléments pour exécuter les étapes du processus de génération.

 Les éléments sont déclarés dans le fichier projet en créant un élément avec le nom du type d’élément comme enfant d’un élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Par exemple, le code suivant crée un type d'élément nommé `Compile` et composé de deux fichiers.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Les types d’éléments peuvent être référencés dans tout le fichier projet à l’aide de la syntaxe @ ( \<ItemType> ). Par exemple, le type d'élément dans l'exemple serait référencé avec la syntaxe `@(Compile)`.

 Dans MSBuild, les noms d'éléments et des attributs respectent la casse. En revanche, ce n'est pas le cas pour les noms de propriétés, d'items et de métadonnées. L'exemple suivant crée le type d'élément `Compile`, `comPile` ou toute autre variation au niveau de la casse, et la valeur « one.cs;two.cs » est affectée au type d'item.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Les éléments peuvent être déclarés à l'aide de caractères génériques et peuvent contenir des métadonnées supplémentaires dans le cas de scénarios de génération plus avancés. Pour plus d’informations sur les éléments, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Tâches

 Les tâches sont des unités de code exécutable que les projets MSBuild utilisent pour effectuer des opérations de génération. Par exemple, une tâche peut compiler des fichiers d'entrée ou exécuter un outil externe. Les tâches peuvent être réutilisées et partagées par plusieurs développeurs dans différents projets.

 La logique d’exécution d’une tâche est écrite en code managé et mappée à MSBuild à l’aide de l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md) . Vous pouvez écrire votre propre tâche en créant un type managé qui implémente l'interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations sur l’écriture de tâches, consultez [écriture de tâches](../msbuild/task-writing.md).

 MSBuild comprend des tâches courantes que vous pouvez modifier en fonction de vos besoins. Voici des exemples : [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source Visual C#. Pour obtenir la liste des tâches disponibles ainsi que des informations sur l’utilisation, consultez [référence des tâches](../msbuild/msbuild-task-reference.md).

 Une tâche est exécutée dans un fichier projet MSBuild en créant un élément qui a le nom de la tâche comme enfant d’un élément [target](../msbuild/target-element-msbuild.md) . En général, les tâches acceptent les paramètres passés comme des attributs de l’élément. Les propriétés et les éléments MSBuild peuvent être utilisés en tant que paramètres. Par exemple, le code suivant appelle la tâche [MakeDir](../msbuild/makedir-task.md) et lui transmet la valeur de la propriété `BuildDir` déclarée dans l’exemple précédent.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Pour plus d’informations sur les tâches, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Compilé

 Les cibles regroupent les tâches selon un ordre particulier et exposent les sections du fichier projet comme points d’entrée du processus de génération. Les cibles sont souvent groupées en sections logiques afin d'accroître la lisibilité et de permettre une expansion. L'éclatement des étapes de génération en plusieurs cibles permet d'appeler une partie du processus de génération à partir d'autres cibles sans copier cette section de code dans chaque cible. Par exemple, si plusieurs points d'entrée du processus de génération requièrent la génération de références, vous pouvez créer une cible qui génère les références et exécuter cette cible à partir de chaque point d'entrée nécessaire.

 Les cibles sont déclarées dans le fichier projet avec l’élément [Target](../msbuild/target-element-msbuild.md). Par exemple, le code suivant crée une cible nommée `Compile`, qui appelle ensuite la tâche [Csc](../msbuild/csc-task.md) comportant la liste d’éléments déclarée dans l’exemple précédent.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Dans des scénarios plus avancés, les cibles peuvent être utilisées pour décrire les relations entre chacune d'elles et exécuter une analyse de dépendance, qui permet d'ignorer des sections entières du processus de génération si la cible correspondante est à jour. Pour plus d’informations sur les cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Journaux d’activité de génération

 Vous pouvez consigner les erreurs de build, les avertissements et les messages dans la console ou un autre périphérique de sortie. Pour plus d’informations, consultez [obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md) et [journalisation dans MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Utiliser MSBuild dans Visual Studio

 Visual Studio utilise le format de fichier projet MSBuild pour stocker les informations de génération relatives aux projets managés. Les paramètres de projet ajoutés ou modifiés à l’aide de l’interface Visual Studio sont reflétés dans le *. \* fichier proj* généré pour chaque projet. Visual Studio utilise une instance hébergée de MSBuild pour générer des projets managés. Cela signifie qu’un projet managé peut être généré dans Visual Studio ou à partir d’une invite de commandes (même si Visual Studio n’est pas installé), et les résultats sont identiques.

 Pour suivre un didacticiel sur l’utilisation de MSBuild dans Visual Studio, consultez la [Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> MULTICIBLAGE

 À l’aide de Visual Studio, vous pouvez compiler une application pour qu’elle s’exécute sur n’importe quelle version de .NET Framework. Par exemple, vous pouvez compiler une application pour qu’elle s’exécute sur .NET Framework 2,0 sur une plateforme 32 bits, et vous pouvez compiler la même application pour qu’elle s’exécute sur .NET Framework 4,5 sur une plateforme 64 bits. Le multi-ciblage désigne la possibilité de compiler en plusieurs Frameworks.

 Voici une partie des avantages offerts par le multi-ciblage :

- Vous pouvez développer des applications qui ciblent des versions antérieures de .NET Framework, par exemple, les versions 2,0, 3,0 et 3,5.

- Vous pouvez cibler des frameworks autres que .NET Framework, par exemple Silverlight.

- Vous pouvez cibler un *profil Framework*, qui est un sous-ensemble prédéfini d’une version cible de .NET Framework.

- Si un Service Pack pour la version actuelle de .NET Framework est libéré, vous pouvez le cibler.

- Le multi-ciblage garantit qu'une application utilise uniquement les fonctionnalités qui sont disponibles dans le framework et la plateforme cibles.

Pour plus d’informations, consultez l’article [Multiciblage de MSBuild](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Voir aussi

| Titre | Description |
| - | - |
| [Procédure pas à pas : Créer un fichier projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Indique comment créer de façon incrémentielle un fichier projet de base, en utilisant uniquement un éditeur de texte. |
| [Procédure pas à pas : Utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md) | Présente les composantes de MSBuild et indique comment écrire, manipuler et déboguer des projets MSBuild sans fermer l'IDE de Visual Studio. |
| [Concepts MSBuild](../msbuild/msbuild-concepts.md) | Présente les quatre composantes de MSBuild : propriétés, éléments, cibles et tâches. |
| [Éléments](../msbuild/msbuild-items.md) | Décrit les concepts généraux sous-jacents au format de fichier MSBuild et la façon dont les éléments s’imbriquent. |
| [MSBuild (propriétés)](../msbuild/msbuild-properties.md) | Présente les propriétés et les collections de propriétés. Les propriétés sont des paires clé/valeur qui peuvent être utilisées pour configurer les générations. |
| [Cibles](../msbuild/msbuild-targets.md) | Explique comment grouper les tâches dans un ordre particulier et autoriser des sections du processus de génération à être appelées sur la ligne de commande. |
| [Tâches](../msbuild/msbuild-tasks.md) | Montre comment créer une unité de code exécutable qui peut être utilisée par MSBuild pour effectuer des opérations de génération atomiques. |
| [Conditions](../msbuild/msbuild-conditions.md) | Explique comment utiliser l'attribut `Condition` dans un élément MSBuild. |
| [Concepts avancés](../msbuild/msbuild-advanced-concepts.md) | Présente le traitement par lot, l'exécution de transformations, le multiciblage, ainsi que d'autres techniques avancées. |
| [Journalisation dans MSBuild](../msbuild/logging-in-msbuild.md) | Décrit comment consigner des événements, des messages et des erreurs de build. |
| [Comment MSBuild génère des projets](build-process-overview.md) | Décrit le processus de génération interne utilisé dans MSBuild |
| [Ressources supplémentaires](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Répertorie les ressources de communauté et de prise en charge pour des informations supplémentaires sur MSBuild. |

## <a name="reference"></a>Référence

- [Référence MSBuild](../msbuild/msbuild-reference.md)\
 Renvoie aux rubriques contenant les informations de référence.

- [Glossaire](msbuild-glossary.md)\
 Définit les termes courants relatifs à MSBuild.
