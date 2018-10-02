---
title: 'CA2119 : Scellez les méthodes qui satisfont les interfaces privées | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 894d35e4d475485b05ba84eb687c967b97044428
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589754"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119 : Scellez les méthodes qui satisfont les interfaces privées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2119 : Scellez les méthodes qui satisfont les interfaces privées](https://docs.microsoft.com/visualstudio/code-quality/ca2119-seal-methods-that-satisfy-private-interfaces).

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public pouvant être hérité fournit une implémentation de méthode substituable d’une `internal` (`Friend` en Visual Basic) interface.

## <a name="rule-description"></a>Description de la règle
 Méthodes d’interface ont une accessibilité publique, qui ne peut pas être modifiée par le type d’implémentation. Une interface interne crée un contrat qui n’est pas destiné à être implémentée en dehors de l’assembly qui définit l’interface. Un type public qui implémente une méthode d’une interface interne à l’aide de la `virtual` (`Overridable` en Visual Basic) modificateur permet à la méthode être substituée par un type dérivé qui est en dehors de l’assembly. Si un deuxième type dans l’assembly de définition appelle la méthode et attend un contrat interne uniquement, le comportement peut être compromis lorsque, au lieu de cela, la méthode substituée dans l’assembly externe est exécutée. Cette opération crée une faille de sécurité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly en utilisant l’une des opérations suivantes :

-   Créez le type déclarant `sealed` (`NotInheritable` en Visual Basic).

-   Modifiez l’accessibilité du type déclarant à `internal` (`Friend` en Visual Basic).

-   Supprimez tous les constructeurs publics du type déclarant.

-   Implémentez la méthode sans utiliser le `virtual` modificateur.

-   Implémentez explicitement la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si, après un examen minutieux, aucun problème de sécurité qui peut être exploitable que si la méthode est substituée en dehors de l’assembly.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `BaseImplementation`, qui enfreint cette règle.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant exploite l’implémentation de méthode virtuelle de l’exemple précédent.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Interfaces](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfaces](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)



