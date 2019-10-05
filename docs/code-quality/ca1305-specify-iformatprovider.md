---
title: 'CA1305 : Spécifier IFormatProvider'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235035"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305 : Spécifier IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode ou un constructeur appelle un ou plusieurs membres qui ont des surcharges qui <xref:System.IFormatProvider?displayProperty=fullName> acceptent un paramètre, et la méthode ou le constructeur n’appelle pas la surcharge <xref:System.IFormatProvider> qui prend le paramètre.

Cette règle ignore les appels aux méthodes .net qui sont documentées comme ignorant <xref:System.IFormatProvider> le paramètre. La règle ignore également les méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Description de la règle

Lorsqu’un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objet <xref:System.IFormatProvider> ou n’est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l’effet souhaité dans tous les paramètres régionaux. En outre, les membres .NET choisissent la culture et la mise en forme par défaut en fonction des hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture en respectant les instructions suivantes :

- Si la valeur est affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si la valeur est stockée et accessible par le logiciel (conservée dans un fichier ou une base de données), utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si vous ne connaissez pas la destination de la valeur, faites en sorte que le consommateur de données ou le fournisseur spécifie la culture.

Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documenté automatiquement et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utilisez la surcharge qui prend un <xref:System.IFormatProvider> argument. Vous pouvez utiliser une [ C# chaîne interpolée](/dotnet/csharp/tutorials/string-interpolation) et la passer à la <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle lorsqu’il est certain que le format par défaut est le bon choix, et où la maintenabilité du code n’est pas une priorité de développement importante.

## <a name="example"></a>Exemple

Dans le code suivant, la `example1` chaîne ne respecte pas la règle ca1305. La `example2` chaîne respecte la règle ca1305 en passant <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, qui implémente <xref:System.IFormatProvider>, à <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. La `example3` chaîne respecte la règle ca1305 en passant une chaîne interpolée à <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Règles associées

- [CA1304 Spécifier CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)