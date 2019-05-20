---
title: 'CA1027 : Marquer les enums avec FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdb8406d43f90414cf255abae6f1ca5f549e92e
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842483"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027 : Marquer les enums avec FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Les valeurs d’une énumération sont des puissances de deux ou des combinaisons d’autres valeurs sont définies dans l’énumération, et le <xref:System.FlagsAttribute?displayProperty=fullName> attribut n’est pas présent. Pour réduire les faux positifs, cette règle ne signale pas d’une violation pour les énumérations qui ont des valeurs contiguës.

Par défaut, cette règle examine uniquement les énumérations publiques, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Appliquer <xref:System.FlagsAttribute> à une énumération lorsque ses constantes nommées peuvent être combinées. Par exemple, considérez une énumération des jours de la semaine dans une application qui effectue le suivi des ressources de chaque jour sont disponibles. Si la disponibilité de chaque ressource est encodée à l’aide de l’énumération a <xref:System.FlagsAttribute> présent, n’importe quelle combinaison de jours peut être représentée. Sans l’attribut, un seul jour de la semaine peut être représenté.

Pour les champs qui stockent des énumérations combinables, les valeurs d’énumération individuelles sont traitées comme des groupes de bits dans le champ. Par conséquent, ces champs sont parfois appelés *des champs de bits*. Pour combiner des valeurs d’énumération pour le stockage dans un champ de bits, utilisez les opérateurs booléens conditionnels. Pour tester un champ de bits pour déterminer si une valeur d’énumération spécifique est présente, utilisez les opérateurs logiques booléens. Pour un champ de bits stocker et récupérer correctement les valeurs d’énumération combinées, chaque valeur est définie dans l’énumération doit être une puissance de deux. Sauf si cela est le cas, les opérateurs logiques booléens ne sera pas en mesure d’extraire les valeurs d’énumération individuelles qui sont stockés dans le champ.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez <xref:System.FlagsAttribute> à l’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle si vous ne souhaitez pas que les valeurs d’énumération soient combinables.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

Dans l’exemple suivant, `DaysEnumNeedsFlags` est une énumération qui satisfait les conditions d’utilisation <xref:System.FlagsAttribute> mais n’est pas. Le `ColorEnumShouldNotHaveFlag` énumération n’a pas de valeurs qui sont des puissances de deux, mais spécifie de manière incorrecte <xref:System.FlagsAttribute>. Cela viole la règle [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Règles associées

- [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.FlagsAttribute?displayProperty=fullName>