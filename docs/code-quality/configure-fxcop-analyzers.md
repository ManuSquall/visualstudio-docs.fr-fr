---
title: Configurer des analyseurs FxCop à l’aide de editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 68c175a55c9e60e870a5466a831aaae50d62dced
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293447"
---
# <a name="configure-fxcop-analyzers"></a>Configurer les analyseurs FxCop

Les [analyseurs FxCop](install-fxcop-analyzers.md) se composent des règles « FxCop » les plus importantes de l’analyse héritée, converties en analyseurs de code .NET Compiler Platform. Vous pouvez configurer des analyseurs de code FxCop de deux manières :

- Avec un [ensemble de règles](#fxcop-analyzer-rule-sets), qui vous permet d’activer ou de désactiver la règle et de définir la gravité des violations de règles individuelles.

- À partir de la version 2.6.3 du package NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) , par le biais d’un [fichier. editorconfig](#editorconfig-file). Les [options configurables](fxcop-analyzer-options.md) vous permettent d’affiner les parties de votre code base à analyser.

> [!TIP]
> Pour plus d’informations sur les différences entre l’analyse héritée et les analyseurs FxCop, consultez [FAQ des analyseurs FxCop](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Ensembles de règles de l’analyseur FxCop

L’une des méthodes permettant de configurer les analyseurs FxCop consiste à utiliser un *ensemble de règles*XML. Un ensemble de règles est un regroupement de règles d’analyse du code qui identifient des problèmes ciblés et des conditions spécifiques. Les ensembles de règles vous permettent d’activer ou de désactiver la règle et de définir la gravité des violations de règles individuelles.

Le package NuGet de l’analyseur FxCop comprend des ensembles de règles prédéfinis pour les catégories de règles suivantes :

- design
- documentation
- facilité de gestion
- affecter des noms
- performances
- fiabilité
- security
- utilisation

Pour plus d’informations, consultez [ensembles de règles pour les analyseurs de code](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Fichier EditorConfig

Vous pouvez configurer les règles de l’analyseur FxCop en ajoutant des paires clé-valeur à un fichier [. editorconfig](https://editorconfig.org) . Un fichier de configuration peut être [spécifique à un projet](#per-project-configuration) ou peut être [partagé](#shared-configuration) entre plusieurs projets.

> [!NOTE]
> Vous ne pouvez pas configurer les règles FxCop héritées à l’aide d’un fichier. editorconfig.

### <a name="per-project-configuration"></a>Configuration par projet

Pour activer la configuration de l’analyseur basé sur editorconfig pour un projet spécifique, ajoutez un fichier *. editorconfig* au répertoire racine du projet.

> [!TIP]
> Vous pouvez ajouter un fichier. editorconfig à votre projet en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions** et en sélectionnant **Ajouter** > **un nouvel élément**. Dans la fenêtre **Ajouter un nouvel élément** , entrez **editorconfig** dans la zone de recherche. Sélectionnez le modèle **fichier editorconfig (par défaut)** , puis choisissez **Ajouter**.
>
> ![Ajouter un élément editorconfig au projet dans Visual Studio](media/add-editorconfig-file.png)

Actuellement, il n’existe pas de prise en charge hiérarchique pour la « combinaison » de fichiers. editorconfig qui existent à différents niveaux de répertoire, par exemple, le niveau de la solution et du projet.

### <a name="shared-configuration"></a>Configuration partagée

Vous pouvez partager un fichier. editorconfig pour la configuration de l’analyseur FxCop entre deux projets ou plus, mais cela nécessite des étapes supplémentaires.

1. Enregistrez le fichier *. editorconfig* dans un emplacement commun.

2. Créez un fichier *. props* avec le contenu suivant :

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

3. Ajoutez une ligne à votre fichier. *csproj* ou *. vbproj* pour importer le fichier *. props* que vous avez créé à l’étape précédente. Cette ligne doit être placée avant toutes les lignes qui importent les fichiers *. props* de l’analyseur FxCop. Par exemple, si votre fichier. props est nommé *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Rechargez le projet.

> [!NOTE]
> L’emplacement partagé arbitraire du fichier EditorConfig décrit ici s’applique uniquement à la configuration des analyseurs FxCop. Pour les autres paramètres, tels que la mise en retrait et le style de code, le fichier EditorConfig doit toujours être placé dans le dossier du projet ou dans un dossier parent.

## <a name="option-scopes"></a>Étendues des options

Chaque option peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, affectation de noms ou conception) ou pour une règle spécifique.

### <a name="all-rules"></a>Toutes les règles

La syntaxe de configuration d’une option pour toutes les règles est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Catégorie de règles

La syntaxe permettant de configurer une option pour une *catégorie* de règles (par exemple, le nom, la conception ou la performance) est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Règle spécifique

La syntaxe de configuration d’une option pour une règle spécifique est la suivante :

|Syntaxe|Exemples|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Voir aussi

- [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analyseurs FxCop](install-fxcop-analyzers.md)
- [Conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
