---
title: Configurer des analyseurs de la qualité du code .NET à l’aide de editorconfig
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035428"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>Configurer l’analyse de la qualité du code .NET avec EditorConfig

Chaque analyseur de qualité du code (dont les ID de règle commencent par `CA` ) peut être affiné pour s’appliquer aux parties de votre code base par le biais d’options configurables. Chaque option est spécifiée en ajoutant une paire clé-valeur à un fichier [baEditorConfig](https://editorconfig.org) . Un fichier de configuration peut être spécifique à un fichier, à un projet, à une solution ou à l’ensemble du référentiel.

> [!TIP]
> Ajoutez un fichier. editorconfig à votre projet en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions** et en sélectionnant **Ajouter**  >  **un nouvel élément**. Dans la fenêtre **Ajouter un nouvel élément** , entrez **editorconfig** dans la zone de recherche. Sélectionnez le modèle **fichier editorconfig (par défaut)** , puis choisissez **Ajouter**.
>
> ![Ajouter un fichier EditorConfig au projet dans Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Pour plus d’informations sur la configuration de la gravité d’une règle (par exemple, s’il s’agit d’une erreur ou d’un avertissement), consultez [définir la gravité de la règle dans un fichier baEditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou bien, vous pouvez choisir l’un des [fichiers EditorConfig intégrés ou des ensembles de règles](analyzer-rule-sets.md) pour activer ou désactiver rapidement une catégorie de règles.

::: moniker-end

Le reste de cet article décrit la syntaxe générale pour les options qui affinent l’application des analyseurs de qualité du code .NET.

## <a name="option-scopes"></a>Étendues des options

Chaque option d’affinage peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, la sécurité ou la conception) ou pour une règle spécifique.

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

## <a name="enabling-editorconfig-based-configuration"></a>Activation de la configuration basée sur EditorConfig

La configuration de l’analyseur basé sur EditorConfig peut être activée pour les étendues suivantes :

- Document (s) spécifique (s)
- Dossier (s) spécifique (s)
- Projet (s) spécifique (s)
- Solution (s) spécifique (s)
- Référentiel entier

Pour activer la configuration, ajoutez un fichier *. editorconfig* avec les options dans le répertoire correspondant. Ce fichier peut également contenir des entrées de configuration du niveau de gravité de diagnostic EditorConfig. Consultez [ce document](use-roslyn-analyzers.md#configure-severity-levels) pour plus d’informations.

## <a name="enable-a-category-of-rules"></a>Activer une catégorie de règles

Les packages de l’analyseur peuvent inclure des fichiers de [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) et/ou d' [ensemble de règles](using-rule-sets-to-group-code-analysis-rules.md) prédéfinis qui permettent d’activer rapidement et facilement une catégorie de règles, telles que des règles de sécurité ou de conception. Le package de l’analyseur NuGet [Microsoft. CodeAnalysis. netanalyzer](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) contient à la fois les fichiers EditorConfig et les ensembles de règles. En activant une catégorie spécifique de règles, vous pouvez identifier des problèmes ciblés et des conditions spécifiques.

> [!NOTE]
> L’activation des règles de l’analyseur et la définition de leur gravité à l’aide d’un fichier EditorConfig sont prises en charge à partir de Visual Studio 2019 version 16,3.

Le package NuGet netanalyzer contient des fichiers EditorConfig prédéfinis et des ensembles de règles pour les catégories de règles suivantes :

- Toutes les règles
- Dataflow
- Conception
- Documentation
- Globalisation
- Interopérabilité
- Maintenabilité
- Dénomination
- Performances
- Porté depuis FxCop
- Fiabilité
- Sécurité
- Utilisation

Chacune de ces catégories de règles a un fichier de EditorConfig ou d’ensemble de règles pour :

- Activer toutes les règles de la catégorie (et désactiver toutes les autres règles)
- Utilisez la gravité par défaut de chaque règle et activez le paramètre par défaut (et désactivez toutes les autres règles).

> [!TIP]
> La catégorie « toutes les règles » dispose d’un EditorConfig ou d’un fichier d’ensemble de règles supplémentaire pour désactiver toutes les règles. Utilisez ce fichier pour supprimer rapidement les avertissements ou erreurs de l’analyseur dans un projet.

> [!TIP]
> Si vous effectuez une migration à partir d’une analyse « FxCop » héritée vers une analyse de code basée sur .NET Compiler Platform, les fichiers EditorConfig et d’ensemble de règles vous permettent de continuer à utiliser des configurations de règles similaires à [celles que vous avez utilisées précédemment](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Fichiers EditorConfig prédéfinis

Les fichiers EditorConfig prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer sont situés dans le répertoire *% UserProfile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* . Par exemple, le fichier EditorConfig pour activer toutes les règles de sécurité se trouve à l’emplacement *% UserProfile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copiez le fichier. editorconfig choisi dans le répertoire racine de votre projet.

## <a name="predefined-rule-sets"></a>Ensembles de règles prédéfinis

Les fichiers d’ensemble de règles prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer sont situés dans le répertoire *% UserProfile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* Par exemple, le fichier de l’ensemble de règles permettant d’activer toutes les règles de sécurité se trouve dans *% UserProfile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.RuleSet*.

Copiez un ou plusieurs ensembles de règles et collez-les dans le répertoire qui contient votre projet Visual Studio ou directement dans **Explorateur de solutions**.

Vous pouvez également [personnaliser un ensemble de règles prédéfini](how-to-create-a-custom-rule-set.md) à votre convenance. Par exemple, vous pouvez modifier la gravité d’une ou plusieurs règles afin que les violations apparaissent en tant qu’erreurs ou avertissements dans le **liste d’erreurs**.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Options d’étendue de règle pour les analyseurs de qualité du code .NET

Vous pouvez spécifier des options dans un [fichier EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project). Par exemple, vous pouvez spécifier les options suivantes.

> [!TIP]
> Pour afficher la liste complète des options disponibles, consultez ce [fichier Configuration.MD de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Voici un exemple de la façon dont une option est documentée dans le fichier Configuration.md de l' *analyseur* :
>
> Nom de l’option : `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valeurs d’option : valeurs intégrales \
> Valeur par défaut : spécifique à chaque règle configurable (« 100000 » par défaut pour la plupart des règles) \
> Exemple : `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| La partie de la surface d’API à analyser | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Séparez plusieurs valeurs par une virgule (,) | `public` | CA1000 [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md) [CA1](ca1000.md)<br/>[CA1012](ca1012.md) - [1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[Ca1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) ca--le ca- [1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [ca1717](ca1717.md)<br/>[Ca1720](ca1720.md) [ca1721s](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[Ca1802](ca1802.md) [-1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer les méthodes asynchrones qui ne retournent pas de valeur | `true`<br/>`false` | `false` | [Ca2007](ca2007.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut exclure les [paramètres de type](/dotnet/csharp/programming-guide/generics/generic-type-parameters) à un seul caractère de la règle, par exemple `S` dans `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie que le code d’un projet qui génère ce type d’assembly doit être analysé | Un ou plusieurs champs de l' <xref:Microsoft.CodeAnalysis.OutputKind> énumération<br/><br/>Séparez plusieurs valeurs par une virgule (,) | Tous les types de sortie | [Ca2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie les modificateurs requis pour les API qui doivent être analysées | Une ou plusieurs valeurs de la table de modificateurs autorisées ci-dessous<br/><br/>Séparez plusieurs valeurs par une virgule (,) | Dépend de chaque règle | [CA1802](ca1802.md) |

| Modificateur autorisé | Résumé |
| --- | --- |
| `none` | Aucune exigence de modificateur |
| `static` ou `Shared` | Doit être déclaré comme « static » (« Shared » dans Visual Basic) |
| `const` | Doit être déclarée comme’const' |
| `readonly` | Doit être déclaré comme’ReadOnly' |
| `abstract` | Doit être déclaré comme’abstract' |
| `virtual` | Doit être déclaré comme’Virtual' |
| `override` | Doit être déclarée comme’override' |
| `sealed` | Doit être déclaré comme’sealed' |
| `extern` | Doit être déclaré en tant que’extern' |
| `async` | Doit être déclarée comme’Async' |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer l’analyse pour le `this` paramètre des méthodes d’extension | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Les noms des méthodes de validation de vérification de valeur null qui valident les arguments passés à la méthode sont non null | Formats de nom de méthode autorisés (séparés par `|` ) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec un `M:` préfixe facultatif | Aucun | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des méthodes de mise en forme de chaînes supplémentaires | Formats de nom de méthode autorisés (séparés par `|` ) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec un `M:` préfixe facultatif | Aucun | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Les noms des types, de telle sorte que le type et tous ses types dérivés soient exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec un `T:` préfixe facultatif | Aucun | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe « M : » pour les méthodes, le préfixe « T : » pour les types, le préfixe « N : » pour les espaces de noms, etc.<br/> - `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques | Aucun | [CA1062](ca1062.md) [CA1303](ca1303.md) [Ca2](ca2000.md) [ca2100](ca2100.md) [ca2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [ca3002](ca3002.md) - [3003](ca3003.md) [ca3004](ca3004.md)<br/>[Ca3005](ca3005.md) [ca3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [ca3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles non autorisés dans le contexte de l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe « M : » pour les méthodes, le préfixe « T : » pour les types, le préfixe « N : » pour les espaces de noms, etc.<br/> - `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques | Aucun | [CA1031](ca1031.md) |

## <a name="see-also"></a>Voir aussi

- [Configuration des analyseurs](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
