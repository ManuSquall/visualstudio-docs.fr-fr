---
title: "CA2111&#160;: Les pointeurs ne doivent pas &#234;tre visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111&#160;: Les pointeurs ne doivent pas &#234;tre visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un champ <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> public ou protégé n'est pas en lecture seule.  
  
## Description de la règle  
 <xref:System.IntPtr> et <xref:System.UIntPtr> sont des types pointeur utilisés pour accéder à une mémoire non managée.  Si un pointeur n'est pas privé, interne ou en lecture seule, un code malveillant peut modifier la valeur du pointeur, autorisant potentiellement l'accès aux emplacements arbitraires en mémoire ou provoquant des défaillances des applications ou du système.  
  
 Si vous projetez de sécuriser l'accès au type qui contient le champ de pointeur, consultez [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Comment corriger les violations  
 Sécurisez le pointeur en le rendant interne, privé ou en lecture seule.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si votre design ne repose pas sur la valeur du pointeur.  
  
## Exemple  
 Le code suivant présente des pointeurs qui violent et satisfont la règle.  Notez que les pointeurs non privés violent également la règle [CA1051 : Ne pas déclarer de champs d'instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Règles connexes  
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051 : Ne pas déclarer de champs d'instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Voir aussi  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>