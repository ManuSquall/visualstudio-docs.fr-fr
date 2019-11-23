---
title: 'Ca1305 : spécifier IFormatProvider | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661445"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305 : Spécifier IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode ou un constructeur appelle un ou plusieurs membres qui ont des surcharges qui acceptent un paramètre <xref:System.IFormatProvider?displayProperty=fullName>, et la méthode ou le constructeur n’appelle pas la surcharge qui prend le paramètre <xref:System.IFormatProvider>. Cette règle ignore les appels aux méthodes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] qui sont documentées comme ignorant le paramètre <xref:System.IFormatProvider> et en outre les méthodes suivantes :

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un objet <xref:System.Globalization.CultureInfo?displayProperty=fullName> ou <xref:System.IFormatProvider> n’est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l’effet souhaité dans tous les paramètres régionaux. De plus, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] membres choisissent la culture et la mise en forme par défaut en fonction des hypothèses qui peuvent ne pas être correctes pour votre code. Pour vous assurer que le code fonctionne comme prévu pour vos scénarios, vous devez fournir des informations spécifiques à la culture en respectant les instructions suivantes :

- Si la valeur est affichée à l’utilisateur, utilisez la culture actuelle. Consultez <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Si la valeur est stockée et accessible par le logiciel (conservée dans un fichier ou une base de données), utilisez la culture dite indifférente. Consultez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Si vous ne connaissez pas la destination de la valeur, faites en sorte que le consommateur de données ou le fournisseur spécifie la culture.

  Notez que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> est utilisé uniquement pour récupérer des ressources localisées à l’aide d’une instance de la classe <xref:System.Resources.ResourceManager?displayProperty=fullName>.

  Même si le comportement par défaut du membre surchargé est adapté à vos besoins, il est préférable d’appeler explicitement la surcharge spécifique à la culture afin que votre code soit documenté automatiquement et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez la surcharge qui prend un <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> et spécifiez l’argument en fonction des indications répertoriées précédemment.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsqu’il est certain que le fournisseur de format/culture par défaut est le bon choix et où la maintenabilité du code n’est pas une priorité de développement importante.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` provoque deux violations de cette règle. `GoodMethod` corrige la première violation en passant la culture dite indifférente à <xref:System.String.Compare%2A>et corrige la deuxième violation en passant la culture actuelle à <xref:System.String.ToLower%2A>, car `string3` est affiché à l’utilisateur.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de la culture actuelle sur le <xref:System.IFormatProvider> par défaut qui est sélectionné par le type de <xref:System.DateTime>.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Cet exemple produit la sortie suivante.

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Règles associées
 [CA1304 : Spécifier CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Voir aussi
 [PLUME : utilisation de la classe CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
