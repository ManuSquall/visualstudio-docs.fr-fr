---
title: "CA2216&#160;: Les types pouvant &#234;tre supprim&#233;s doivent d&#233;clarer un finaliseur | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216&#160;: Les types pouvant &#234;tre supprim&#233;s doivent d&#233;clarer un finaliseur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> et présente des champs qui laissent entendre l'utilisation de ressources non managées, n'implémente pas de finaliseur conforme à la description de <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## Description de la règle  
 Une violation de cette règle est rapportée si le type supprimable contient des champs des types suivants :  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez un finaliseur qui appelle votre méthode <xref:System.IDisposable.Dispose%2A>.  
  
## Quand supprimer les avertissements  
 ll est possible de supprimer sans risque un avertissement de cette règle si le type n'implémente pas <xref:System.IDisposable> en vue de libérer des ressources non managées.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Règles connexes  
 [CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816 : Appeler GC.SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049 : Les types qui possèdent des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)