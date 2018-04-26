---
title: 'CA1305 : Spécifier IFormatProvider'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da4125a87ea7fe1576834dacc14af9a1a1861206
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305 : Spécifier IFormatProvider
|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un <xref:System.IFormatProvider?displayProperty=fullName> paramètre et la méthode ou le constructeur n’appelle pas la surcharge qui accepte le <xref:System.IFormatProvider> paramètre. Cette règle ignore les appels aux [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] méthodes sont documentées comme ignorant le <xref:System.IFormatProvider> paramètre et, en outre, les méthodes suivantes :

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un <xref:System.Globalization.CultureInfo?displayProperty=fullName> ou <xref:System.IFormatProvider> objet n’est pas fourni, la valeur par défaut fournie par le membre surchargé n’est peut-être pas l’effet que vous souhaitez dans tous les paramètres régionaux. En outre, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] membres choisissent la culture par défaut et la mise en forme en fonction d’hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture selon les consignes suivantes :

-   Si la valeur doit être affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Si la valeur est stockée et accessibles par logiciel (persistante dans un fichier ou d’une base de données), utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Si vous ne connaissez pas la destination de la valeur, ont le consommateur de données ou le fournisseur de spécifier la culture.

 Notez que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

 Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documentés et plus facile à maintenir.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> et spécifiez l’argument selon les règles qui ont été citées plus haut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque vous êtes certain que le fournisseur de format/culture par défaut est le bon choix et où la maintenabilité du code n’est pas une priorité de développement importants.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente pour <xref:System.String.Compare%2A>et corrige la deuxième violation en passant la culture actuelle à <xref:System.String.ToLower%2A> car `string3` est affiché à l’utilisateur.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de la culture en cours sur la valeur par défaut <xref:System.IFormatProvider> qui est sélectionné par le <xref:System.DateTime> type.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]

 Cet exemple produit la sortie suivante.

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Règles associées
 [CA1304 : Spécifier CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Voir aussi
[À l’aide de la classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)