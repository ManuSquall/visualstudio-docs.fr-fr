---
title: 'CA1033 : les méthodes d’interface doivent pouvoir être appelées par les types enfants | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542296"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom.

## <a name="rule-description"></a>Description de la règle
 Prenons l’exemple d’un type de base qui implémente explicitement une méthode d’interface publique. Un type qui dérive du type de base peut accéder à la méthode d’interface héritée uniquement par le biais d’une référence à l’instance actuelle ( `this` en C#) qui est castée en interface. Si le type dérivé réimplémente (explicitement) la méthode d’interface héritée, l’implémentation de base ne peut plus être accédée. L’appel via la référence d’instance actuelle appellera l’implémentation dérivée ; Cela provoque une récurrence et un dépassement de capacité de la pile.

 Cette règle ne signale pas de violation pour une implémentation explicite de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lorsqu’une méthode ou une méthode visible de l’extérieur `Close()` `System.IDisposable.Dispose(Boolean)` est fournie.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez une nouvelle méthode qui expose les mêmes fonctionnalités et qui est visible pour les types dérivés ou passez à une implémentation non explicite. Si une modification avec rupture est acceptable, une alternative consiste à rendre le type sealed.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si une méthode visible de l’extérieur est fournie et a les mêmes fonctionnalités, mais avec un nom différent de celui de la méthode implémentée explicitement.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `ViolatingBase` , qui enfreint la règle et un type, `FixedBase` , qui affiche un correctif pour la violation.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
