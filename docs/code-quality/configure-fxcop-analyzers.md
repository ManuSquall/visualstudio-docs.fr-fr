---
title: Configurez des analyseurs FxCop à l’aide d’editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816913"
---
# <a name="configure-fxcop-analyzers"></a>Configurez des analyseurs FxCop

Le [analyseurs FxCop](install-fxcop-analyzers.md) se composent des règles de « FxCop » plus importantes d’analyse statique du code, converti en analyseurs de Roslyn. Vous pouvez configurer les analyseurs de code FxCop de deux manières :

- Avec un [ensemble de règles](#fxcop-analyzer-rule-sets), qui vous permet d’activer ou désactiver la règle et définir le niveau de gravité des violations des règles individuelles.

- Depuis la version 2.6.3 de la [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) de package NuGet, via un [fichier .editorconfig](#editorconfig-file). Le [options configurables](fxcop-analyzer-options.md) permettent de vous affinez les parties de votre base de code pour analyser.

> [!TIP]
> Pour plus d’informations sur les différences entre l’analyse du code statique FxCop et les analyseurs FxCop, consultez [Forum aux questions sur les analyseurs FxCop](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Ensembles de règles FxCop analyzer

La première consiste à configurer les analyseurs FxCop en utilisant un XML *ensemble de règles*. Un ensemble de règles est un regroupement de règles d’analyse du code qui identifient les problèmes ciblés et des conditions spécifiques. Ensembles de règles vous permettent d’activer ou désactiver la règle et définir le niveau de gravité des violations des règles individuelles.

Le package NuGet d’analyseur FxCop inclut les ensembles de règles prédéfinies pour les catégories suivantes :

- design
- documentation
- facilité de gestion
- affecter des noms
- performances
- fiabilité
- security
- utilisation

Pour plus d’informations, consultez [des ensembles de règles pour les analyseurs de Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Fichier EditorConfig

Vous pouvez configurer des règles de l’analyseur en ajoutant les paires clé-valeur à un [.editorconfig](https://editorconfig.org) fichier. Un fichier de configuration peut être [spécifiques à un projet](#per-project-configuration) ou il peut être [partagé](#shared-configuration) entre deux ou plusieurs projets.

### <a name="per-project-configuration"></a>Configuration par projet

Pour activer la configuration de l’analyseur basé sur les .editorconfig pour un projet spécifique, ajoutez un *.editorconfig* fichier vers le répertoire du projet racine.

> [!TIP]
> Vous pouvez ajouter un fichier .editorconfig à votre projet en cliquant sur le projet dans **l’Explorateur de solutions** et en sélectionnant **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** fenêtre, entrez **editorconfig** dans la zone de recherche. Sélectionnez le **editorconfig fichier (par défaut)** modèle et choisissez **ajouter**.
>
> ![Ajouter un élément d’editorconfig au projet dans Visual Studio](media/add-editorconfig-file.png)

Il n’existe actuellement aucune prise en charge hiérarchique pour « combinant » .editorconfig des fichiers qui existent au niveau des répertoires différents, par exemple, le niveau de la solution et projet.

### <a name="shared-configuration"></a>Configuration partagée

Vous pouvez partager un fichier .editorconfig pour la configuration de l’analyseur entre deux ou plusieurs projets, mais il requiert quelques étapes supplémentaires.

1. Enregistrer le *.editorconfig* fichier à un emplacement commun.

2. Créer un *.props* fichier avec le contenu suivant :

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Ajoutez une ligne à votre *.csproj* ou *.vbproj* fichier à importer le *.props* fichier que vous avez créé à l’étape précédente. Cette ligne doit être placée avant toutes les lignes qui importent l’Analyseur de FxCop *.props* fichiers. Par exemple, si votre fichier .props se nomme *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Recharger le projet.

> [!NOTE]
> Vous ne pouvez pas configurer les règles FxCop héritées (analyse du code statique FxCop) à l’aide d’un fichier .editorconfig.

## <a name="option-scopes"></a>Étendues de l’option

Chaque option peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, d’affectation de noms ou de la conception) ou pour une règle spécifique.

### <a name="all-rules"></a>Toutes les règles

La syntaxe de configuration d’une option pour toutes les règles est comme suit :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Catégorie de règles

La syntaxe de configuration d’une option pour un *catégorie* de règles (par exemple, d’affectation de noms, création ou performances) se présente comme suit :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Règle spécifique

La syntaxe de configuration d’une option pour une règle spécifique est comme suit :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Voir aussi

- [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analyseurs FxCop](install-fxcop-analyzers.md)
