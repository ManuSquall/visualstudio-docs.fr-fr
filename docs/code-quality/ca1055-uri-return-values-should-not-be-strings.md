---
title: 'CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45d9874316ec2a22f875e2ba4fe7d5406ff916c6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547342"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’une méthode contient «URI», «Uri», «URN», «URN», «URL» ou «URL», et la méthode retourne une chaîne.

Par défaut, cette règle examine uniquement les méthodes publiques, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Cette règle fractionne le nom de la méthode en jetons en fonction de la Convention de casse Pascal et vérifie si chaque jeton est égal à «URI», «Uri», «URN», «URN», «URL» ou «URL». En cas de correspondance, la règle part du principe que la méthode retourne un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La <xref:System.Uri?displayProperty=fullName> classe fournit ces services de manière sûre et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez le type de retour par <xref:System.Uri>un.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si la valeur de retour ne représente pas un URI.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un type, `ErrorProne`, qui enfreint cette règle et un type, `SaferWay`, qui satisfait la règle.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Règles associées

- [CA1056 Les propriétés URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054 Les paramètres URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234 Passer des objets System. URI à la place de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057 Les surcharges d’URI de chaîne appellent les surcharges de System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)