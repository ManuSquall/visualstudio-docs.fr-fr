---
title: 'CA1304 : spécifier CultureInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661470"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304 : Spécifier CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode ou un constructeur appelle un membre qui a une surcharge qui accepte un paramètre <xref:System.Globalization.CultureInfo?displayProperty=fullName>, et la méthode ou le constructeur n’appelle pas la surcharge qui prend le paramètre <xref:System.Globalization.CultureInfo>. Cette règle ignore les appels aux méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un objet <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=fullName> n’est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l’effet souhaité dans tous les paramètres régionaux. De plus, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] membres choisissent la culture et la mise en forme par défaut en fonction des hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture en respectant les instructions suivantes :

- Si la valeur est affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Si la valeur est stockée et accessible par le logiciel, c’est-à-dire rendue persistante dans un fichier ou une base de données, utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Si vous ne connaissez pas la destination de la valeur, faites en sorte que le consommateur de données ou le fournisseur spécifie la culture.

  Notez que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la classe <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documenté automatiquement et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez la surcharge qui prend un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> et spécifiez l’argument en fonction des indications répertoriées précédemment.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsqu’il est certain que le fournisseur de format/culture par défaut est le bon choix, et où la maintenabilité du code n’est pas une priorité de développement importante.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente à System. String. Compare, et corrige la deuxième violation en passant la culture actuelle à <xref:System.String.ToLower%2A>, car `string3` est affiché à l’utilisateur.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de la culture actuelle sur le <xref:System.IFormatProvider> par défaut qui est sélectionné par le type de <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Cet exemple produit la sortie suivante.

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Règles associées
 [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Voir aussi
 [PLUME : utilisation de la classe CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
