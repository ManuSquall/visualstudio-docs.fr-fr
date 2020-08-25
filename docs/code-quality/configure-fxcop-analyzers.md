---
title: Configurer des analyseurs de qualité du code .NET à l’aide de editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800734"
---
# <a name="configure-net-code-quality-analyzers"></a>Configurer des analyseurs de qualité du code .NET

Pour certains analyseurs de la qualité du code .NET (ceux dont les ID de règle commencent par `CA` ), vous pouvez affiner les parties de votre code base auxquelles ils doivent s’appliquer via des [options configurables](fxcop-analyzer-options.md). Chaque option est spécifiée en ajoutant une paire clé-valeur à un fichier [baEditorConfig](https://editorconfig.org) . Un fichier de configuration peut être spécifique à un fichier, à un projet, à une solution ou à l’ensemble du référentiel.

> [!TIP]
> Ajoutez un fichier. editorconfig à votre projet en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions** et en sélectionnant **Ajouter**  >  **un nouvel élément**. Dans la fenêtre **Ajouter un nouvel élément** , entrez **editorconfig** dans la zone de recherche. Sélectionnez le modèle **fichier editorconfig (par défaut)** , puis choisissez **Ajouter**.
>
> ![Ajouter un fichier editorconfig au projet dans Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Pour plus d’informations sur la configuration de la gravité d’une règle (par exemple, s’il s’agit d’une erreur ou d’un avertissement), consultez [définir la gravité de la règle dans un fichier baEditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou bien, vous pouvez choisir l’un des [fichiers EditorConfig intégrés ou des ensembles de règles](analyzer-rule-sets.md) pour activer ou désactiver rapidement une catégorie de règles.

::: moniker-end

Le reste de cet article décrit la syntaxe générale pour les [options qui affinent](fxcop-analyzer-options.md) l’application des analyseurs de qualité du code .net.

## <a name="option-scopes"></a>Étendues des options

Chaque option d’affinage peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, attribution d’un nom ou conception) ou pour une règle spécifique.

### <a name="all-rules"></a>Toutes les règles

La syntaxe de configuration d’une option pour *toutes les* règles est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality. Nomoptin = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Catégorie de règles

La syntaxe permettant de configurer une option pour une *catégorie* de règles (par exemple, le nom, la conception ou la performance) est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality. RuleCategory. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Règle spécifique

La syntaxe de configuration d’une option pour une règle *spécifique* est la suivante :

|Syntaxe|Exemple|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>Activation de la configuration basée sur Editorconfig

La configuration de l’analyseur basé sur EditorConfig peut être activée pour les étendues suivantes :

- Document (s) spécifique (s)
- Dossier (s) spécifique (s)
- Projet (s) spécifique (s)
- Solution (s) spécifique (s)
- Référentiel entier

Pour activer la configuration, ajoutez un fichier *. editorconfig* avec les options dans le répertoire correspondant. Ce fichier peut également contenir des entrées de configuration du niveau de gravité de diagnostic EditorConfig. Consultez [ce document](use-roslyn-analyzers.md#rule-severity) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

- [Options d’étendue de règle pour les analyseurs de qualité du code .NET](fxcop-analyzer-options.md)
- [Configuration des analyseurs](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
