---
title: "CA2111 : Les pointeurs ne doivent pas être visibles | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 31ae25892b6b5a153a0a4d1e52047eb5be2368d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111 : Les pointeurs ne doivent pas être visibles
|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un public ou protégé <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> champ n’est pas en lecture seule.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.IntPtr>et <xref:System.UIntPtr> sont des types pointeur qui sont utilisés pour accéder à la mémoire non managée. Si un pointeur n’est pas privé, interne ou en lecture seule, un code malveillant peut modifier la valeur du pointeur, potentiellement autorisant l’accès aux emplacements arbitraires en mémoire ou provoquant des défaillances des applications ou du système.  
  
 Si vous projetez de sécuriser l’accès au type qui contient le champ de pointeur, consultez [CA2112 : les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sécurisez le pointeur en le rendant en lecture seule, interne ou privé.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle si vous ne comptez pas sur la valeur du pointeur.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre des pointeurs qui violent et satisfont la règle. Notez que les pointeurs non privés violent également la règle [CA1051 : ne pas déclarer de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>