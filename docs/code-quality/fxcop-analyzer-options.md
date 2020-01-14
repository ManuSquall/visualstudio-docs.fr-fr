---
title: Options de configuration de l’analyseur FxCop
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9e87ec97acd7aa0ab668c0840aec8bbd84df7e9e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587626"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Options d’étendue de règle pour les analyseurs FxCop

Certaines règles de l’analyseur FxCop vous permettent d’affiner les parties de votre code base à appliquer. Cette page répertorie les options de configuration d’étendue disponibles, leurs valeurs autorisées et les règles auxquelles elles peuvent être appliquées. Pour utiliser ces options, spécifiez-les dans un [fichier EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Ces options de configuration sont disponibles à partir de la version 2.6.3 du package NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Pour afficher la liste complète des options disponibles pour une version donnée du package FxCopAnalyzers, examinez le fichier Configuration.md de l' *analyseur* dans le dossier *documentation* du package. Le fichier se trouve à l’emplacement *% UserProfile%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\documentation\Analyzer configuration.MD*. Ce fichier de documentation de configuration est inclus dans chaque version du package, à partir de la version 2.6.5. Voici un exemple de la façon dont une option est documentée dans le fichier Configuration.md de l' *analyseur* :
>
> Nom de l’option : `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valeurs d’option : valeurs intégrales \
> Valeur par défaut : spécifique à chaque règle configurable (« 100000 » par défaut pour la plupart des règles) \
> Exemple : `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| La partie de la surface d’API à analyser | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Séparez plusieurs valeurs par une virgule (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer les méthodes asynchrones qui ne retournent pas de valeur | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut exclure les [paramètres de type](/dotnet/csharp/programming-guide/generics/generic-type-parameters) à un seul caractère de la règle, par exemple, `S` dans `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie que le code d’un projet qui génère ce type d’assembly doit être analysé | Un ou plusieurs champs de l’énumération <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Séparez plusieurs valeurs par une virgule (,) | Tous les types de sortie | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie les modificateurs requis pour les API qui doivent être analysées | Une ou plusieurs valeurs de la table de modificateurs autorisées ci-dessous<br/><br/>Séparez plusieurs valeurs par une virgule (,) | Dépend de chaque règle | [CA1802](ca1802.md) |

| Modificateur autorisé | Récapitulatif |
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
| Indique s’il faut ignorer l’analyse pour le paramètre `this` des méthodes d’extension | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Les noms des méthodes de validation de vérification de valeur null qui valident les arguments passés à la méthode sont non null | Formats de nom de méthode autorisés (séparés par `|`) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec préfixe `M:` facultatif | Aucun | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des méthodes de mise en forme de chaînes supplémentaires | Formats de nom de méthode autorisés (séparés par `|`) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec préfixe `M:` facultatif | Aucun | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Les noms des types, de telle sorte que le type et tous ses types dérivés soient exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|`) :<br/> -Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec préfixe `T:` facultatif | Aucun | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|`) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe « M : » pour les méthodes, le préfixe « T : » pour les types, le préfixe « N : » pour les espaces de noms, etc.<br/> - `.ctor` pour les constructeurs et les `.cctor` pour les constructeurs statiques | Aucun | [CA1062](ca1062.md) [CA1303](ca1303.md) [Ca2](ca2000.md) [ca2100](ca2100.md) [ca2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [ca3002](ca3002.md) - [3003](ca3003.md) [ca3004](ca3004.md)<br/>[Ca3005](ca3005.md) [ca3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [ca3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles non autorisés dans le contexte de l’analyse | Formats de noms de symboles autorisés (séparés par `|`) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe « M : » pour les méthodes, le préfixe « T : » pour les types, le préfixe « N : » pour les espaces de noms, etc.<br/> - `.ctor` pour les constructeurs et les `.cctor` pour les constructeurs statiques | Aucun | [CA1031](ca1031.md) |

