---
title: "CA2002 : Ne verrouillent pas sur des objets à identité faible | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 54a7693f5e2921b7cab60278c870c456084c56f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002 : Ne définissez pas un verrou sur des objets à identité faible
|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|CheckId|CA2002|  
|Catégorie|Microsoft.Reliability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un thread tente d’acquérir un verrou sur un objet qui a une identité faible.  
  
## <a name="rule-description"></a>Description de la règle  
 Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet. Les types suivants ont une identité faible et sont signalés par la règle :  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, utiliser un objet d’un type qui n’est pas dans la liste dans la section Description.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="related-rules"></a>Règles associées  
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre des verrous d’objet qui enfreint la règle.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [lock, instruction](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [SyncLock (instruction)](/dotnet/visual-basic/language-reference/statements/synclock-statement)