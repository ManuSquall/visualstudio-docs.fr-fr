---
title: "CA2119&#160;: Scellez les m&#233;thodes qui satisfont les interfaces priv&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2119&#160;: Scellez les m&#233;thodes qui satisfont les interfaces priv&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public pouvant être hérité fournit une implémentation de méthode pouvant être substituée d'une interface `internal` \(`Friend` en Visual Basic\).  
  
## Description de la règle  
 Les méthodes d'interface disposent d'une accessibilité publique, qui ne peut pas être modifiée par le type d'implémentation.  Une interface interne crée un contrat qui n'est pas destiné à être implémenté à l'extérieur de l'assembly qui définit l'interface.  Un type public qui implémente une méthode d'une interface interne à l'aide du modificateur `virtual` \(`Overridable` en Visual Basic\) autorise la substitution de la méthode par un type dérivé situé à l'extérieur de l'assembly.  Si un deuxième type dans l'assembly de définition appelle la méthode et s'attend à un contrat interne uniquement, le comportement peut être compromis lorsque la méthode substituée dans l'assembly externe est exécutée.  Cela crée une faille de sécurité.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, empêchez la substitution de la méthode à l'extérieur de l'assembly à l'aide de l'une des méthodes suivantes :  
  
-   Créez le type déclarant `sealed` \(`NotInheritable` en Visual Basic\).  
  
-   Remplacez l'accessibilité du type déclarant par `internal` \(`Friend` en Visual Basic\).  
  
-   Supprimez tous les constructeurs publics du type déclarant.  
  
-   Implémentez la méthode sans utiliser le modificateur `virtual`.  
  
-   Implémentez explicitement la méthode.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si, après examen minutieux, aucun problème de sécurité, qui peut être exploitable si la méthode est substituée à l'extérieur de l'assembly, n'est détecté.  
  
## Exemple  
 L'exemple suivant présente un type, `BaseImplementation`, qui ne respecte pas cette règle.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Exemple  
 L'exemple suivant exploite l'implémentation de méthode virtuelle de l'exemple précédent.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## Voir aussi  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)