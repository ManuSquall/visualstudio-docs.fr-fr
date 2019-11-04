---
title: 'CA2119 : Scellez les méthodes qui satisfont les interfaces privées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af41fc5576cbcd56589680d99c0cd5c0dfd6e6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664769"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119 : Scellez les méthodes qui satisfont les interfaces privées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public pouvant être hérité fournit une implémentation de méthode substituable d’une interface `internal` (`Friend` dans Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Les méthodes d’interface ont une accessibilité publique, qui ne peut pas être modifiée par le type d’implémentation. Une interface interne crée un contrat qui n’est pas destiné à être implémenté en dehors de l’assembly qui définit l’interface. Un type public qui implémente une méthode d’une interface interne à l’aide du modificateur `virtual` (`Overridable` dans Visual Basic) permet à la méthode d’être substituée par un type dérivé qui est en dehors de l’assembly. Si un deuxième type de l’assembly de définition appelle la méthode et attend un contrat uniquement interne, le comportement risque d’être compromis quand, à la place, la méthode substituée dans l’assembly externe est exécutée. Cela crée une faille de sécurité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly à l’aide de l’un des éléments suivants :

- Définissez le type déclarant `sealed` (`NotInheritable` dans Visual Basic).

- Modifiez l’accessibilité du type déclarant en `internal` (`Friend` dans Visual Basic).

- Supprimez tous les constructeurs publics du type déclarant.

- Implémentez la méthode sans utiliser le modificateur `virtual`.

- Implémentez la méthode explicitement.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si, après examen attentif, il n’existe aucun problème de sécurité susceptible d’être exploitable si la méthode est substituée en dehors de l’assembly.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `BaseImplementation`, qui enfreint cette règle.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant exploite l’implémentation de méthode virtuelle de l’exemple précédent.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfaces](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
