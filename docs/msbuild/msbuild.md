---
title: MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633068"
---
# <a name="msbuild"></a>MSBuild

Le moteur Microsoft Build est une plate-forme pour la construction d’applications. Ce moteur, également appelé MSBuild, fournit un schéma XML pour un fichier projet qui contrôle la manière dont la plateforme de génération traite et génère les logiciels. Visual Studio utilise MSBuild, mais MSBuild ne dépend pas de Visual Studio. En invoquant *msbuild.exe* sur votre fichier de projet ou de solution, vous pouvez orchestrer et construire des produits dans des environnements où Visual Studio n’est pas installé.

 Visual Studio utilise MSBuild pour charger et générer des projets managés. Les fichiers projet de Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* et autres) contiennent du code XML MSBuild qui s’exécute lors de la génération d’un projet avec l’environnement IDE. Les projets Visual Studio importent tous les paramètres et processus de génération nécessaires pour effectuer le travail de développement classique, mais vous pouvez les développer ou les modifier à partir de Visual Studio ou en utilisant un éditeur XML.

 Pour plus d’informations sur MSBuild pour LE CD, voir [MSBuild (C)](/cpp/build/msbuild-visual-cpp).

 Les exemples suivants illustrent quand vous pourriez exécuter des builds en invoquant MSBuild de la ligne de commande au lieu de l’IDE Visual Studio.

- Visual Studio n'est pas installé. ([Télécharger MSBuild sans Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Vous souhaitez utiliser la version 64 bits de MSBuild. Cette version MSBuild est généralement inutile, mais elle permet à MSBuild d'accéder à plus de mémoire.

- Vous souhaitez exécuter une build dans plusieurs processus. Toutefois, vous pouvez utiliser l'IDE pour obtenir le même résultat sur les projets dans C++ et C#.

- Vous souhaitez modifier le système de génération. Par exemple, vous pouvez souhaiter effectuer les actions suivantes :

  - Prétraitez les fichiers avant qu'ils n'atteignent le compilateur.

  - Copiez les sorties de génération à un autre emplacement.

  - Créez des fichiers compressés à partir des sorties de génération.

  - Procédez à une étape de post-traitement. Par exemple, vous pouvez souhaiter horodater un assembly avec une version différente.

Vous pouvez écrire du code dans l'IDE de Visual Studio, mais les générations s'exécutent à l'aide de MSBuild. Comme une autre alternative, vous pouvez construire du code dans l’IDE sur un ordinateur de développement, mais exécuter MSBuild à partir de la ligne de commande pour construire du code qui est intégré à partir de plusieurs développeurs. Vous pouvez également utiliser [l’interface de ligne de commande .NET Core (CLI),](/dotnet/core/tools/)qui utilise MSBuild, pour construire des projets .NET Core.

> [!NOTE]
> Vous pouvez utiliser Azure Pipelines pour compiler, tester et déployer automatiquement votre application. Votre système de génération peut automatiquement exécuter des générations lorsque les développeurs archivent du code (par exemple, dans le cadre d'une stratégie continue d'intégration) ou selon une planification (par exemple, une build nocturne de test de vérification de build). Azure Pipelines compile votre code à l’aide de MSBuild. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

Cet article donne un aperçu de MSBuild. Pour un didacticiel d’introduction, consultez la [Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Utiliser MSBuild dans une invite de commandes

 Pour exécuter MSBuild à une invite de commande, passez un fichier de projet à *MSBuild.exe*, ainsi que les options appropriées de ligne de commande. Les options de ligne de commande vous permettent de définir des propriétés, d'exécuter des cibles spécifiques et de définir d'autres options qui contrôlent le processus de génération. Par exemple, la syntaxe de ligne de commande suivante permet de générer le fichier *MyProj.proj* avec la propriété `Configuration` définie sur `Debug`.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Pour plus d’informations sur les options de ligne de commande MSBuild, voir [référence de la ligne de commandement](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Avant de télécharger un projet, déterminez la crédibilité du code.

## <a name="project-file"></a>Fichier projet

 MSBuild utilise un format de fichier de projet basé sur XML qui est simple et extensible. Le format de fichier de projet MSBuild permet aux développeurs de décrire les éléments qui doivent être construits, ainsi que la façon dont ils doivent être construits pour différents systèmes d’exploitation et configurations. De plus, le format de fichier projet permet aux développeurs de créer des règles de génération réutilisables qui peuvent être réparties en fichiers distincts, de telle sorte que les builds puissent être exécutées de façon cohérente sur différents projets du produit.

 Les sections suivantes décrivent certains des éléments de base du format de fichier du projet MSBuild. Pour un tutoriel sur la façon de créer un fichier de projet de base, voir [Procédure pas à pas: Créer un fichier de projet MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)à partir de zéro .

### <a name="properties"></a>Propriétés de <a name="BKMK_Properties"></a>

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

 L’ensemble du fichier projet peut comporter des références à des propriétés suivant la syntaxe $(\<nom_propriété>). Par exemple, vous pouvez référencer les propriétés dans les exemples précédents en utilisant `$(BuildDir)` et `$(Configuration)`.

 Pour plus d’informations sur les propriétés, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a>Articles

 Les éléments sont des entrées du système de génération qui représentent généralement des fichiers. Les éléments sont regroupés en types d’éléments basés sur des noms d’objets définis par l’utilisateur. Ces types d’éléments peuvent être utilisés comme paramètres des tâches, lesquelles utilisent les éléments pour exécuter les étapes du processus de génération.

 Les éléments sont déclarés dans le fichier projet en créant un élément avec le nom du type d’élément comme enfant d’un élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Par exemple, le code suivant crée un type d'élément nommé `Compile` et composé de deux fichiers.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 L’ensemble du fichier projet peut comporter des références à des types d’éléments suivant la syntaxe @(\<type_élément>). Par exemple, le type d'élément dans l'exemple serait référencé avec la syntaxe `@(Compile)`.

 Dans MSBuild, les noms d'éléments et des attributs respectent la casse. En revanche, ce n'est pas le cas pour les noms de propriétés, d'items et de métadonnées. L'exemple suivant crée le type d'élément `Compile`, `comPile` ou toute autre variation au niveau de la casse, et la valeur « one.cs;two.cs » est affectée au type d'item.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Les éléments peuvent être déclarés à l'aide de caractères génériques et peuvent contenir des métadonnées supplémentaires dans le cas de scénarios de génération plus avancés. Pour plus d’informations sur les éléments, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a>Tâches

 Les tâches sont des unités de code exécutable que les projets MSBuild utilisent pour effectuer des opérations de construction. Par exemple, une tâche peut compiler des fichiers d'entrée ou exécuter un outil externe. Les tâches peuvent être réutilisées et partagées par plusieurs développeurs dans différents projets.

 La logique d’exécution d’une tâche est écrite dans le code géré et cartographiée à MSBuild en utilisant [l’élément UsingTask.](../msbuild/usingtask-element-msbuild.md) Vous pouvez écrire votre propre tâche en créant un type managé qui implémente l'interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations sur la façon d’écrire des tâches, voir [l’écriture de tâches](../msbuild/task-writing.md).

 MSBuild comprend des tâches courantes que vous pouvez modifier en fonction de vos besoins. Voici des exemples : [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source Visual C#. Pour une liste des tâches disponibles ainsi que des informations d’utilisation, voir [référence de tâche](../msbuild/msbuild-task-reference.md).

 Une tâche est exécutée dans un fichier de projet MSBuild en créant un élément qui a le nom de la tâche en tant qu’enfant d’un élément [cible.](../msbuild/target-element-msbuild.md) En général, les tâches acceptent les paramètres passés comme des attributs de l’élément. Les propriétés et les articles MSBuild peuvent être utilisés comme paramètres. Par exemple, le code suivant appelle la tâche [MakeDir](../msbuild/makedir-task.md) et lui transmet la valeur de la propriété `BuildDir` déclarée dans l’exemple précédent.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Pour plus d’informations sur les tâches, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a>Cibles

 Les cibles regroupent les tâches selon un ordre particulier et exposent les sections du fichier projet comme points d’entrée du processus de génération. Les cibles sont souvent groupées en sections logiques afin d'accroître la lisibilité et de permettre une expansion. L'éclatement des étapes de génération en plusieurs cibles permet d'appeler une partie du processus de génération à partir d'autres cibles sans copier cette section de code dans chaque cible. Par exemple, si plusieurs points d'entrée du processus de génération requièrent la génération de références, vous pouvez créer une cible qui génère les références et exécuter cette cible à partir de chaque point d'entrée nécessaire.

 Les cibles sont déclarées dans le fichier projet avec l’élément [Target](../msbuild/target-element-msbuild.md). Par exemple, le code suivant crée une cible nommée `Compile`, qui appelle ensuite la tâche [Csc](../msbuild/csc-task.md) comportant la liste d’éléments déclarée dans l’exemple précédent.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Dans des scénarios plus avancés, les cibles peuvent être utilisées pour décrire les relations entre chacune d'elles et exécuter une analyse de dépendance, qui permet d'ignorer des sections entières du processus de génération si la cible correspondante est à jour. Pour plus d’informations sur les cibles, consultez l’article [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Journaux d’activité de génération

 Vous pouvez consigner les erreurs de build, les avertissements et les messages dans la console ou un autre périphérique de sortie. Pour plus d’informations, voir [Obtenir des journaux de construction](../msbuild/obtaining-build-logs-with-msbuild.md) et [l’enregistrement dans MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Utiliser MSBuild dans Visual Studio

 Visual Studio utilise le format de fichier de projet MSBuild pour stocker des informations sur les projets gérés. Les paramètres du projet qui sont ajoutés ou modifiés à l’aide de l’interface Visual Studio sont reflétés dans le *.\* fichier proj* qui est généré pour chaque projet. Visual Studio utilise une instance hébergée de MSBuild pour construire des projets gérés. Cela signifie qu’un projet géré peut être construit dans Visual Studio ou à une invite de commande (même si Visual Studio n’est pas installé), et les résultats seront identiques.

 Pour suivre un didacticiel sur l’utilisation de MSBuild dans Visual Studio, consultez la [Procédure pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Multitargeting

 En utilisant Visual Studio, vous pouvez compiler une application pour exécuter sur l’une des nombreuses versions de .NET Framework. Par exemple, vous pouvez compiler une application pour exécuter sur .NET Framework 2.0 sur une plate-forme 32 bits, et vous pouvez compiler la même application pour exécuter sur .NET Framework 4.5 sur une plate-forme 64 bits. Le multi-ciblage désigne la possibilité de compiler en plusieurs Frameworks.

 Voici une partie des avantages offerts par le multi-ciblage :

- Vous pouvez développer des applications qui ciblent les versions antérieures de .NET Framework, par exemple, les versions 2.0, 3.0 et 3.5.

- Vous pouvez cibler des cadres autres que .NET Framework, par exemple, Silverlight.

- Vous pouvez cibler un *profil Framework*, qui est un sous-ensemble prédéfini d’une version cible de .NET Framework.

- Si un pack de service pour la version actuelle de .NET Framework est publié, vous pouvez le cibler.

- Le multi-ciblage garantit qu'une application utilise uniquement les fonctionnalités qui sont disponibles dans le framework et la plateforme cibles.

Pour plus d’informations, consultez l’article [Multiciblage de MSBuild](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Voir aussi

| Intitulé | Description |
| - | - |
| [Procédure pas à pas : Création d’un fichier de projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Indique comment créer de façon incrémentielle un fichier projet de base, en utilisant uniquement un éditeur de texte. |
| [Procédures pas à pas : utilisation de MSBuild](../msbuild/walkthrough-using-msbuild.md) | Présente les composantes de MSBuild et indique comment écrire, manipuler et déboguer des projets MSBuild sans fermer l'IDE de Visual Studio. |
| [Concepts MSBuild](../msbuild/msbuild-concepts.md) | Présente les quatre composantes de MSBuild : propriétés, éléments, cibles et tâches. |
| [Éléments](../msbuild/msbuild-items.md) | Décrit les concepts généraux derrière le format de fichier MSBuild et comment les pièces s’emboîtent. |
| [Propriétés MSBuild](../msbuild/msbuild-properties.md) | Présente les propriétés et les collections de propriétés. Les propriétés sont des paires clé/valeur qui peuvent être utilisées pour configurer les générations. |
| [Cibles](../msbuild/msbuild-targets.md) | Explique comment grouper les tâches dans un ordre particulier et autoriser des sections du processus de génération à être appelées sur la ligne de commande. |
| [Tâches](../msbuild/msbuild-tasks.md) | Montre comment créer une unité de code exécutable qui peut être utilisé par MSBuild pour effectuer des opérations de construction atomique. |
| [Conditions](../msbuild/msbuild-conditions.md) | Explique comment utiliser l'attribut `Condition` dans un élément MSBuild. |
| [Concepts avancés](../msbuild/msbuild-advanced-concepts.md) | Présente le traitement par lot, l'exécution de transformations, le multiciblage, ainsi que d'autres techniques avancées. |
| [Journalisation dans MSBuild](../msbuild/logging-in-msbuild.md) | Décrit comment consigner des événements, des messages et des erreurs de build. |
| [Ressources supplémentaires](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Répertorie les ressources de communauté et de prise en charge pour des informations supplémentaires sur MSBuild. |

## <a name="reference"></a>Informations de référence

- [Référence MSBuild](../msbuild/msbuild-reference.md)\
 Renvoie aux rubriques contenant les informations de référence.

- [Glossaire](msbuild-glossary.md)\
 Définit les termes courants relatifs à MSBuild.
