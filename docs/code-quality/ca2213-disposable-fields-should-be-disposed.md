---
title: "CA2213&#160;: Les champs pouvant &#234;tre supprim&#233;s doivent l&#39;&#234;tre | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213&#160;: Les champs pouvant &#234;tre supprim&#233;s doivent l&#39;&#234;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs qui constituent des types qui implémentent eux aussi <xref:System.IDisposable>.  La méthode <xref:System.IDisposable.Dispose%2A> du champ n'est pas appelée par la méthode <xref:System.IDisposable.Dispose%2A> du type déclarant.  
  
## Description de la règle  
 Un type est chargé de se débarrasser de toutes ses ressources non managées ; cette opération est effectuée en implémentant <xref:System.IDisposable>.  Cette règle s'assure qu'un type `T` pouvant être supprimé déclare un champ `F` qui constitue une instance d'un type `FT` pouvant être supprimé.  Pour chaque champ `F`, la règle essaie de localiser un appel à `FT.Dispose`.  La règle applique une recherche aux méthodes appelées par `T.Dispose`, et à un niveau inférieur \(les méthodes appelées par les méthodes appelées par `FT.Dispose`\).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur des champs qui constituent des types qui implémentent <xref:System.IDisposable> si vous êtes chargé d'allouer et de libérer les ressources non managées détenues par le champ.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si vous n'êtes pas chargé de libérer la ressource détenue par le champ ou si l'appel à <xref:System.IDisposable.Dispose%2A> se produit à un niveau d'appel inférieur à celui que la règle contrôle.  
  
## Exemple  
 L'exemple suivant présente un type `TypeA` qui implémente <xref:System.IDisposable> \(`FT` dans l'examen précédent\).  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Exemple  
 L'exemple suivant affiche un type `TypeB` qui viole cette règle en déclarant un champ `aFieldOfADisposableType` \(`F` dans la discussion précédente\) comme un type pouvant être supprimé \(`TypeA`\) et en n'appelant pas le champ <xref:System.IDisposable.Dispose%2A>.  `TypeB` correspond à `T` dans la discussion précédente.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)