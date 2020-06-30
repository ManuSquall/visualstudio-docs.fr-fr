---
title: 'CA1003 : utiliser les instances du gestionnaire d’événements génériques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539904"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003 : Utiliser les instances du gestionnaire d'événements génériques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type contient un délégué qui retourne void, dont la signature contient deux paramètres (le premier objet et le deuxième un type qui peut être assigné à EventArgs) et le conteneur cible l’assembly [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Description de la règle
 Avant [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , afin de passer des informations personnalisées au gestionnaire d’événements, il fallait déclarer un nouveau délégué qui spécifiait une classe dérivée de la <xref:System.EventArgs?displayProperty=fullName> classe. Ce n’est plus le cas dans [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , qui a introduit le <xref:System.EventHandler%601?displayProperty=fullName> délégué. Ce délégué générique permet d’utiliser n’importe quelle classe dérivée de <xref:System.EventArgs> pour être utilisée avec le gestionnaire d’événements.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le délégué et remplacez son utilisation à l’aide du <xref:System.EventHandler%601?displayProperty=fullName> délégué. Si le délégué est généré automatiquement par le [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateur, modifiez la syntaxe de la déclaration d’événement pour utiliser le <xref:System.EventHandler%601?displayProperty=fullName> délégué.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un délégué qui enfreint la règle. Dans l' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] exemple, les commentaires décrivent comment modifier l’exemple pour satisfaire la règle. Pour l’exemple C#, l’exemple suivant montre le code modifié.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant supprime la déclaration Delegate de l’exemple précédent, qui répond à la règle, et remplace son utilisation dans les `ClassThatRaisesEvent` méthodes et à `ClassThatHandlesEvent` l’aide du <xref:System.EventHandler%601?displayProperty=fullName> délégué.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : Ne pas exposer de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
