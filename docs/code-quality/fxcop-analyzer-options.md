---
title: Options de configuration de l’analyseur FxCop
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: de4fdbbdf54976ba3ee12c3621f7038cd4704a76
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449061"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Options d’étendue de règle pour les analyseurs FxCop

Certaines règles de l’analyseur FxCop vous permettent d’affiner les parties de votre code base à appliquer. Cette page répertorie les options de configuration d’étendue disponibles, leurs valeurs autorisées et les règles auxquelles elles peuvent être appliquées. Pour utiliser ces options, spécifiez-les dans un [fichier EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Ces options de configuration sont disponibles à partir de la version 2.6.3 du package NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Pour afficher la liste complète des options disponibles pour une version donnée du package FxCopAnalyzers, examinez le fichier Configuration.md de l' *analyseur* dans le dossier *documentation* du package. Le fichier se trouve dans *% UserProfile% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3Version @ no__t-4\documentation\Analyzer configuration.MD*. Ce fichier de documentation de configuration est inclus dans chaque version du package, à partir de la version 2.6.5. Voici un exemple de la façon dont une option est documentée dans le fichier Configuration.md de l' *analyseur* :
>
> Nom de l’option : `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Valeurs d’option : valeurs intégrales \
> Valeur par défaut : spécifique à chaque règle configurable (« 100000 » par défaut pour la plupart des règles) \
> Exemple : `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| La partie de la surface d’API à analyser | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Séparez plusieurs valeurs par une virgule (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer les méthodes asynchrones qui ne retournent pas de valeur | `true`<br/>`false` | `false` | [Ca2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut exclure les [paramètres de type](/dotnet/csharp/programming-guide/generics/generic-type-parameters) à un seul caractère de la règle, par exemple, `S` dans `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> Dans la version 2.6.3 et antérieure du package de l’analyseur, cette option était nommée `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie que le code d’un projet qui génère ce type d’assembly doit être analysé | Un ou plusieurs champs de l’énumération <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Séparez plusieurs valeurs par une virgule (,) | Tous les types de sortie | [Ca2007](ca2007-do-not-directly-await-task.md) |
