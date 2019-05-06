---
title: 'CA1033 : Méthodes d’interface doivent pouvoir être appelées par les types enfants | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e43944a3a21f48559ab5bf36d30585f8550b9da1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938494"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom.

## <a name="rule-description"></a>Description de la règle
 Envisagez un type de base qui implémente explicitement une méthode d’interface publique. Un type qui dérive du type de base peut accéder à la méthode d’interface héritée uniquement par le biais d’une référence à l’instance actuelle (`this` dans C#) qui est converti dans l’interface. Si le type dérivé ré-implémente (explicitement) la méthode d’interface héritée, l’implémentation de base n’est plus est accessible. L’appel de la référence d’instance actuelle appelle l’implémentation dérivée ; Cela provoque la récursivité et un dépassement de capacité de pile.

 Cette règle ne signale pas d’une violation pour une implémentation explicite de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lorsque extérieurement visible `Close()` ou `System.IDisposable.Dispose(Boolean)` méthode est fournie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez une nouvelle méthode qui expose les mêmes fonctionnalités et qui est visible pour les types dérivés ou modifier pour une implémentation non explicites. Si une modification avec rupture est acceptable, une alternative consiste à rendre le type sealed.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si une méthode visible de l’extérieur est fournie qui a les mêmes fonctionnalités, mais un nom différent de la méthode implémentée explicitement.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `ViolatingBase`, qui enfreint la règle et un type, `FixedBase`, qui illustre un correctif pour la violation.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Interfaces](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
