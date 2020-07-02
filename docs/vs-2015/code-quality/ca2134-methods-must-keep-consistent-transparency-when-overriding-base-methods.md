---
title: 'CA2134 : les méthodes doivent conserver une transparence cohérente lors du remplacement des méthodes de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547717"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134 : La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Cette règle se déclenche lorsqu’une méthode marquée avec le <xref:System.Security.SecurityCriticalAttribute> substitue une méthode qui est transparente ou marquée avec <xref:System.Security.SecuritySafeCriticalAttribute> . La règle se déclenche également lorsqu’une méthode qui est transparente ou marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> substitue une méthode marquée avec un <xref:System.Security.SecurityCriticalAttribute> .

 La règle est appliquée lors de la substitution d’une méthode virtuelle ou de l’implémentation d’une interface.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche lors des tentatives de modification de l’accessibilité de la sécurité d’une méthode plus haut dans la chaîne d’héritage. Par exemple, si une méthode virtuelle dans une classe de base est transparente ou critique sécurisée, la classe dérivée doit la substituer avec une méthode transparente ou critique sécurisée. À l’inverse, si le virtuel est critique de sécurité, la classe dérivée doit la remplacer par une méthode critique de sécurité. La même règle s’applique à l’implémentation de méthodes d’interface.

 Les règles de transparence sont appliquées lorsque le code est compilé juste-à-temps au moment de l’exécution, de sorte que le calcul de la transparence n’a pas d’informations de type dynamique. Par conséquent, le résultat du calcul de la transparence doit pouvoir être déterminé uniquement à partir des types statiques qui sont compilés juste-à-temps, quel que soit le type dynamique.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la transparence de la méthode qui remplace une méthode virtuelle ou implémenter une interface pour qu’elle corresponde à la transparence de la méthode virtuelle ou d’interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas les avertissements de cette règle. Les violations de cette règle entraînent un Runtime <xref:System.TypeLoadException> pour les assemblys qui utilisent la transparence de niveau 2.

## <a name="examples"></a>Exemples

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Code transparent de sécurité, niveau 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
