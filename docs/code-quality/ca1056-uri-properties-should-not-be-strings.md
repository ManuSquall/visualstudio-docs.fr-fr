---
title: 'CA1056 : Les propriétés URI ne doivent pas être des chaînes'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ed7da8e9529c4753497d63279901744bb8e0f6e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786135"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056 : Les propriétés URI ne doivent pas être des chaînes

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type déclare une propriété de chaîne dont le nom contient « uri », « Uri », « urn », « Urn », « url » ou « Url ».

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Cette règle fractionne le nom de propriété en jetons basés sur la convention de casse Pascal et vérifie si chaque jeton est égal à « uri », « Uri », « urn », « Urn », « url » ou « Url ». Il existe une correspondance, la règle considère que la propriété représente un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. Le <xref:System.Uri?displayProperty=fullName> classe fournit ces services de manière sûre et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez la propriété à un <xref:System.Uri> type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si la propriété ne représente pas un URI.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1056.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre un type, `ErrorProne`, qui enfreint cette règle et un type, `SaferWay`, qui satisfait la règle.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Règles associées

- [CA1054 : Paramètres de l’URI ne doivent pas être de chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055 : Les valeurs doivent être pas des chaînes de retour URI](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057 : Surcharges d’URI de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)