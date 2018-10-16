---
title: 'CA2134 : Méthodes doivent rester une transparence cohérente lors de la substitution des méthodes de base | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fdb43405cb920510993a3acead454bac366e959d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211789"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134 : La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Cette règle se déclenche lorsqu’une méthode marquée avec le <xref:System.Security.SecurityCriticalAttribute> substitue une méthode qui est transparente ou marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute>. La règle se déclenche également lorsqu’une méthode qui est transparente ou marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> substitue une méthode qui est marquée avec un <xref:System.Security.SecurityCriticalAttribute>.

 La règle est appliquée lors de la substitution d’une méthode virtuelle ou de l’implémentation d’une interface.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur les tentatives de modification de l’accessibilité de sécurité d’une méthode supplémentaire pour la chaîne d’héritage. Par exemple, si une méthode virtuelle dans une classe de base est transparent ou critique sécurisé, puis la classe dérivée doit remplacer avec une méthode transparente ou critique sécurisé. À l’inverse, si le serveur virtuel est critique de sécurité, la classe dérivée doit substituer avec une méthode critique de sécurité. La même règle s’applique pour l’implémentation des méthodes d’interface.

 Règles de transparence sont appliqués lorsque le code est JIT compilé au lieu de lors de l’exécution, afin que le calcul de la transparence n’a pas d’informations de type dynamique. Par conséquent, le résultat du calcul de transparence doit pouvoir être déterminé uniquement à partir des types statiques qui est compilé par JIT, quel que soit le type dynamique.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier la transparence de la méthode qui est une méthode virtuelle ou en implémentant une interface pour correspondre à la transparence du serveur virtuel ou une méthode d’interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas les avertissements de cette règle. Les violations de cette règle provoquent un runtime <xref:System.TypeLoadException> pour les assemblys qui utilisent la transparence de niveau 2.

## <a name="examples"></a>Exemples

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Code Transparent de sécurité, niveau 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



