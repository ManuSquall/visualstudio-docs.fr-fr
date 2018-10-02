---
title: 'CA2002 : Ne verrouillent pas sur des objets à identité faible | Microsoft Docs'
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
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09e9fd213ca000afb163f37ddb659c0ea5cf3c53
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590312"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002 : Ne définissez pas un verrou sur des objets à identité faible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2002 : ne verrouillent pas sur des objets à identité faible](https://docs.microsoft.com/visualstudio/code-quality/ca2002-do-not-lock-on-objects-with-weak-identity).

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Category|Microsoft.Reliability|
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
 Pour corriger une violation de cette règle, utilisez un objet à partir d’un type qui n’est pas dans la liste dans la section de Description.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Exemple
 L’exemple suivant montre des verrous d’objets qui enfreignent la règle.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [Lock, instruction](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock (instruction)](http://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)



