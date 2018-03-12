---
title: "CA2134 : Transparence des méthodes doivent rester cohérente lors de la substitution de méthodes de base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 62438b49d91f680ae360f1d32f7cfe3b0efa2b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134 : La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Cette règle se déclenche lorsqu’une méthode marquée avec le <xref:System.Security.SecurityCriticalAttribute> substitue une méthode qui est transparente ou marquée à le <xref:System.Security.SecuritySafeCriticalAttribute>. La règle se déclenche également lorsqu’une méthode qui est transparente ou marquée à le <xref:System.Security.SecuritySafeCriticalAttribute> substitue une méthode qui est marquée avec un <xref:System.Security.SecurityCriticalAttribute>.  
  
 La règle est appliquée lors de la substitution d’une méthode virtuelle ou de l’implémentation d’une interface.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle se déclenche sur les tentatives de modification de l’accessibilité de sécurité d’une méthode plus haut de la chaîne d’héritage. Par exemple, si une méthode virtuelle dans une classe de base est transparent ou critique sécurisé, puis la classe dérivée doit remplacer une méthode transparent ou critique sécurisé. À l’inverse, si le serveur virtuel est critique de sécurité, la classe dérivée doit remplacer avec une méthode critique de sécurité. La même règle s’applique pour l’implémentation des méthodes d’interface.  
  
 Règles de transparence sont appliqués lorsque le code est JIT compilé au lieu de lors de l’exécution, afin que le calcul de la transparence n’a pas d’informations de type dynamique. Par conséquent, le résultat du calcul de transparence doit pouvoir être déterminé uniquement à partir des types statiques en cours de compilation JIT, quel que soit le type dynamique.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la transparence de la méthode qui remplace une méthode virtuelle ou implémente une interface pour correspondre à la méthode d’interface ou de transparence du serveur virtuel.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Les violations de cette règle provoquent un runtime <xref:System.TypeLoadException> pour les assemblys qui utilisent la transparence de niveau 2.  
  
## <a name="examples"></a>Exemples  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Code Transparent de sécurité, niveau 2](/dotnet/framework/misc/security-transparent-code-level-2)