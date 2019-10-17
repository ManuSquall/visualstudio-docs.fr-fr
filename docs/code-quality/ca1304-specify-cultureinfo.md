---
title: 'CA1304 : Spécifier CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f4726b21b51b963074ee9ae1c161872f6a5e5a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444438"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304 : Spécifier CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode ou un constructeur appelle un membre qui a une surcharge qui accepte un paramètre <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>, et la méthode ou le constructeur n’appelle pas la surcharge qui prend le paramètre <xref:System.Globalization.CultureInfo>. Cette règle ignore les appels aux méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Description de la règle

Lorsqu’un objet <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=nameWithType> n’est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l’effet souhaité dans tous les paramètres régionaux. En outre, les membres .NET choisissent la culture et la mise en forme par défaut en fonction des hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture en respectant les instructions suivantes :

- Si la valeur est affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si la valeur est stockée et accessible par le logiciel, c’est-à-dire rendue persistante dans un fichier ou une base de données, utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si vous ne connaissez pas la destination de la valeur, faites en sorte que le consommateur de données ou le fournisseur spécifie la culture.

Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documenté automatiquement et plus facile à gérer.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la classe <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un argument <xref:System.Globalization.CultureInfo>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle lorsqu’il est certain que la culture par défaut est le choix approprié et que la maintenabilité du code n’est pas une priorité de développement importante.

## <a name="example-showing-how-to-fix-violations"></a>Exemple illustrant comment corriger les violations

Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente à <xref:System.String.Compare%2A?displayProperty=nameWithType>, et corrige la deuxième violation en passant la culture actuelle à <xref:System.String.ToLower%2A?displayProperty=nameWithType>, car `string3` est affiché pour l’utilisateur.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Exemple d’affichage de la sortie mise en forme

L’exemple suivant montre l’effet de la culture actuelle sur la @no__t par défaut-0 qui est sélectionnée par le type <xref:System.DateTime>.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Cet exemple génère la sortie suivante :

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Règles associées

- [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)
