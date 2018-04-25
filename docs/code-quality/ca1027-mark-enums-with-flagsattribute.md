---
title: 'CA1027 : Marquer les enums avec FlagsAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0660ea1f83360d56633573557e52f40f3751bef5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027 : Marquer les enums avec FlagsAttribute
|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Les valeurs d’une énumération publique sont des puissances de deux ou des combinaisons d’autres valeurs sont définies dans l’énumération, et le <xref:System.FlagsAttribute?displayProperty=fullName> attribut n’est pas présent. Pour réduire les faux positifs, cette règle ne signale pas d’une violation des énumérations qui ont des valeurs contiguës.

## <a name="rule-description"></a>Description de la règle
 Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Appliquer <xref:System.FlagsAttribute> à une énumération lorsque ses constantes nommées peuvent être combinées. Par exemple, considérez une énumération des jours de la semaine dans une application qui effectue le suivi des ressources de chaque jour sont disponibles. Si la disponibilité de chaque ressource est encodée à l’aide de l’énumération a <xref:System.FlagsAttribute> présent, n’importe quelle combinaison de jours pouvant être représenté. Sans l’attribut, un seul jour de la semaine peut être représenté.

 Pour les champs qui stockent des énumérations combinables, les valeurs d’énumération individuelles sont traitées comme des groupes de bits dans le champ. Par conséquent, ces champs sont parfois appelés *champs de bits*. Pour combiner des valeurs d’énumération pour le stockage dans un champ de bits, utilisez les opérateurs booléens conditionnels. Pour tester un champ de bits pour déterminer si une valeur d’énumération spécifique est présente, utilisez les opérateurs logiques booléens. Pour un champ de bits stocker et récupérer correctement les valeurs d’énumération combinées, chaque valeur est définie dans l’énumération doit être une puissance de deux. Sauf si c’est le cas, les opérateurs logiques booléens ne sera pas en mesure d’extraire les valeurs d’énumération individuelles qui sont stockés dans le champ.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez <xref:System.FlagsAttribute> à l’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si vous ne souhaitez pas les valeurs d’énumération ne peut être combiné à.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `DaysEnumNeedsFlags` est une énumération qui satisfait les conditions d’utilisation <xref:System.FlagsAttribute>, mais ne l’a ne pas. Le `ColorEnumShouldNotHaveFlag` énumération n’a pas de valeurs qui sont des puissances de deux, mais spécifie incorrectement <xref:System.FlagsAttribute>. Cela viole la règle [CA2217 : ne marquez pas les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.FlagsAttribute?displayProperty=fullName>