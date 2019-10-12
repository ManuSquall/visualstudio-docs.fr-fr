---
title: Configurer des analyseurs FxCop à l’aide de editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 62dd64dfe4e801f91731b1ed569e3a809156d0d1
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172790"
---
# <a name="configure-fxcop-analyzers"></a>Configurer les analyseurs FxCop

Le [package des analyseurs FxCop](install-fxcop-analyzers.md) se compose des règles « FxCop » les plus importantes de l’analyse héritée convertie en analyseurs de code basés sur .NET Compiler Platform. Pour certaines règles FxCop, vous pouvez affiner les parties de votre code base à laquelle elles doivent être appliquées via les [options configurables](fxcop-analyzer-options.md). Chaque option est spécifiée en ajoutant une paire clé-valeur à un fichier [baEditorConfig](https://editorconfig.org) . Un fichier de configuration peut être [spécifique à un projet](#per-project-configuration) ou peut être [partagé](#shared-configuration) entre plusieurs projets.

> [!TIP]
> Ajoutez un fichier. editorconfig à votre projet en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions** et en sélectionnant **Ajouter** > **nouvel élément**. Dans la fenêtre **Ajouter un nouvel élément** , entrez **editorconfig** dans la zone de recherche. Sélectionnez le modèle **fichier editorconfig (par défaut)** , puis choisissez **Ajouter**.
>
> ![Ajouter un fichier editorconfig au projet dans Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Pour plus d’informations sur la configuration de la gravité d’une règle (par exemple, s’il s’agit d’une erreur ou d’un avertissement), consultez [définir la gravité de la règle dans un fichier baEditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou bien, vous pouvez choisir l’un des [fichiers EditorConfig intégrés ou des ensembles de règles](analyzer-rule-sets.md) pour activer ou désactiver rapidement une catégorie de règles.

::: moniker-end

Le reste de cet article décrit la syntaxe générale pour les [options qui affinent](fxcop-analyzer-options.md) l’application des règles FxCop.

> [!NOTE]
> Vous ne pouvez pas configurer les règles FxCop héritées à l’aide d’un fichier EditorConfig. Pour plus d’informations sur les différences entre l’analyse héritée et les analyseurs FxCop, consultez [FAQ des analyseurs FxCop](fxcop-analyzers-faq.md).

## <a name="option-scopes"></a>Étendues des options

Chaque option d’affinage peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, attribution d’un nom ou conception) ou pour une règle spécifique.

### <a name="all-rules"></a>Toutes les règles

La syntaxe de configuration d’une option pour *toutes les* règles est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Catégorie de règles

La syntaxe permettant de configurer une option pour une *catégorie* de règles (par exemple, le nom, la conception ou la performance) est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Règle spécifique

La syntaxe de configuration d’une option pour une règle *spécifique* est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Configuration par projet

Pour activer la configuration de l’analyseur basé sur EditorConfig pour un projet spécifique, ajoutez un fichier *. EditorConfig* au répertoire racine du projet.

Actuellement, il n’existe pas de prise en charge hiérarchique pour la « combinaison » de fichiers. editorconfig qui existent à différents niveaux de répertoire, par exemple, le niveau de la solution et du projet.

## <a name="shared-configuration"></a>Configuration partagée

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
> L’emplacement partagé arbitraire du fichier EditorConfig décrit ici s’applique uniquement à la configuration de l’étendue de certaines règles de l’analyseur FxCop. Pour les autres paramètres, tels que la gravité de la règle, les paramètres généraux de l’éditeur et le style de code, le fichier EditorConfig doit toujours être placé dans le dossier du projet ou dans un dossier parent.

## <a name="see-also"></a>Voir aussi

- [Options d’étendue de règle pour les analyseurs FxCop](fxcop-analyzer-options.md)
- [Configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analyseurs FxCop](install-fxcop-analyzers.md)
- [Conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
