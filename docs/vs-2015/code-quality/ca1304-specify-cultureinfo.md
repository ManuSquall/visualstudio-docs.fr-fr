---
title: 'CA1304 : Spécifier CultureInfo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d53cdb1622fbb9750cddd2a79b1bbc7cd606ba20
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188337"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304 : Spécifier CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode ou un constructeur appelle un membre qui a une surcharge qui accepte un <xref:System.Globalization.CultureInfo?displayProperty=fullName> paramètre et la méthode ou le constructeur n’appelle pas la surcharge qui accepte le <xref:System.Globalization.CultureInfo> paramètre. Cette règle ignore les appels aux méthodes suivantes :

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Quand un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=fullName> objet n’est pas fourni, la valeur par défaut qui est fournie par le membre surchargé n’est peut-être pas l’effet souhaité dans tous les paramètres régionaux. En outre, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] membres choisissent la culture par défaut et la mise en forme basée sur des hypothèses qui peuvent ne pas être correctes pour votre code. Pour que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture selon les consignes suivantes :

-   Si la valeur doit être affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Si la valeur est stockée et accessibles par le logiciel, c'est-à-dire, rendues persistantes dans un fichier ou d’une base de données, utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Si vous ne connaissez pas la destination de la valeur, ont le consommateur de données ou le fournisseur de spécifier la culture.

 Notez que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

 Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documentés et plus facile à maintenir.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez la surcharge qui accepte un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> et spécifiez l’argument en respectant les instructions qui ont été répertoriés précédemment.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque vous êtes certain que le fournisseur de culture ou le format par défaut est le bon choix, et où la maintenabilité du code n’est pas une priorité de développement importants.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente à System.String.Compare et corrige la seconde en passant la culture actuelle à <xref:System.String.ToLower%2A> car `string3` est affiché à l’utilisateur.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de la culture actuelle sur la valeur par défaut <xref:System.IFormatProvider> qui est sélectionné par le <xref:System.DateTime> type.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Cet exemple produit la sortie suivante.

 **4/6/1900 12 H 15:12**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Règles associées
 [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Voir aussi
 [NIB : À l’aide de la classe CultureInfo](http://msdn.microsoft.com/en-us/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)



