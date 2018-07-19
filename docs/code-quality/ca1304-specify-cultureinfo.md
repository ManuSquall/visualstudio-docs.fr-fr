---
title: 'CA1304 : Spécifier CultureInfo'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bae12da61047e8e9bde6ee097ed84c1d6c95acbc
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174138"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304 : Spécifier CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode ou un constructeur appelle un membre qui a une surcharge qui accepte un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> paramètre et la méthode ou le constructeur n’appelle pas la surcharge qui accepte le <xref:System.Globalization.CultureInfo> paramètre. Cette règle ignore les appels aux méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Description de la règle

Quand un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=nameWithType> objet n’est pas fourni, la valeur par défaut qui est fournie par le membre surchargé n’est peut-être pas l’effet souhaité dans tous les paramètres régionaux. En outre, les membres de .NET Framework choisissent la culture par défaut et mise en forme basée sur des hypothèses qui peuvent ne pas être correctes pour votre code. Pour que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture selon les consignes suivantes :

- Si la valeur doit être affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si la valeur est stockée et accessibles par le logiciel, c'est-à-dire, rendues persistantes dans un fichier ou d’une base de données, utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si vous ne connaissez pas la destination de la valeur, ont le consommateur de données ou le fournisseur de spécifier la culture.

Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documentés et plus facile à maintenir.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la <xref:System.Resources.ResourceManager?displayProperty=nameWithType> classe.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un <xref:System.Globalization.CultureInfo> argument.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle lorsque vous êtes certain que la culture par défaut est le bon choix, et où la maintenabilité du code n’est pas une priorité de développement importants.

## <a name="example-showing-how-to-fix-violations"></a>Exemple montrant comment corriger les violations

Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente pour <xref:System.String.Compare%2A?displayProperty=nameWithType>et corrige la seconde en passant la culture actuelle à <xref:System.String.ToLower%2A?displayProperty=nameWithType> car `string3` est affiché à l’utilisateur.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Affichage de l’exemple de sortie mise en forme

L’exemple suivant montre l’effet de la culture actuelle sur la valeur par défaut <xref:System.IFormatProvider> qui est sélectionné par le <xref:System.DateTime> type.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Cet exemple génère la sortie suivante :

**4/6/1900 12 H 15:12**

**06/04/1900 12:15:12**

## <a name="related-rules"></a>Règles associées

- [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Voir aussi

- [À l’aide de la classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)