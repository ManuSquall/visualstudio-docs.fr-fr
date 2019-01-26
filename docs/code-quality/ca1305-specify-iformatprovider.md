---
title: 'CA1305 : Spécifier IFormatProvider'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 55ecfa146958819092c51055e039f57e8c1b3f6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018707"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305 : Spécifier IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode ou un constructeur appelle un ou plusieurs membres qui ont des surcharges qui acceptent un <xref:System.IFormatProvider?displayProperty=fullName> paramètre et la méthode ou le constructeur n’appelle pas la surcharge qui accepte le <xref:System.IFormatProvider> paramètre.

Cette règle ignore les appels aux méthodes .NET Framework qui sont documentées comme ignorant le <xref:System.IFormatProvider> paramètre. La règle ignore également les méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Description de la règle

Quand un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> ou <xref:System.IFormatProvider> objet n’est pas fourni, la valeur par défaut qui est fournie par le membre surchargé n’est peut-être pas l’effet souhaité dans tous les paramètres régionaux. En outre, les membres de .NET Framework choisissent la culture par défaut et mise en forme basée sur des hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture selon les consignes suivantes :

- Si la valeur doit être affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si la valeur est stockée et accessibles par des logiciels (persistante dans un fichier ou d’une base de données), utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si vous ne connaissez pas la destination de la valeur, ont le consommateur de données ou le fournisseur de spécifier la culture.

Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documentés et plus facile à maintenir.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un <xref:System.IFormatProvider> argument. Ou utilisez un [c# chaîne interpolée](/dotnet/csharp/tutorials/string-interpolation) et transmettez-le à la <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle lorsque vous êtes certain que le format par défaut est le bon choix, et où la maintenabilité du code n’est pas une priorité de développement importants.

## <a name="example"></a>Exemple

Dans le code suivant, le `example1` chaîne viole la règle CA1305. Le `example2` chaîne est conforme aux règles CA1305 en passant <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, qui implémente <xref:System.IFormatProvider>à <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. Le `example3` chaîne est conforme aux règles CA1305 en passant une chaîne interpolée <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

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

- [CA1304 : Spécifier CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Voir aussi

- [À l’aide de la classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)