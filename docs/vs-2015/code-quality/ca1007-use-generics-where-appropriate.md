---
title: 'Ca1007 : utiliser des génériques lorsque cela est approprié | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4ee33305c1ae0f15e5d8f390a4b65d62c87b6904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547938"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007 : Utiliser des classes génériques lorsque cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Une méthode visible de l’extérieur contient un paramètre de référence de type <xref:System.Object?displayProperty=fullName> , et l’assembly conteneur cible [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Description de la règle
 Un paramètre de référence est un paramètre modifié à l’aide du `ref` `ByRef` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] mot clé (in). Le type d’argument fourni pour un paramètre de référence doit correspondre exactement au type de paramètre de référence. Pour utiliser un type dérivé du type de paramètre de référence, le type doit d’abord être casté et assigné à une variable du type de paramètre de référence. L’utilisation d’une méthode générique autorise le passage de tous les types, soumis à des contraintes, à la méthode sans cast préalable du type vers le type de paramètre de référence.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode générique et remplacez le <xref:System.Object> paramètre à l’aide d’un paramètre de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une routine d’échange à usage général qui est implémentée en tant que méthodes génériques et non génériques. Notez l’efficacité des chaînes échangées à l’aide de la méthode générique par rapport à la méthode non générique.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : Ne pas exposer de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
