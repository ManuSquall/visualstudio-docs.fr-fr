---
title: "CA1402&#160;: &#201;viter les surcharges dans les interfaces COM visibles | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402&#160;: &#201;viter les surcharges dans les interfaces COM visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une interface COM \(Component Object Model\) visible déclare des méthodes surchargées.  
  
## Description de la règle  
 Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom.  Les surcharges suivantes sont renommées de manière unique par l'ajout d'un trait de soulignement '\_' au nom et d'un entier qui correspond à l'ordre de déclaration de la surcharge.  Prenons par exemple les méthodes suivantes.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Ces méthodes sont exposées aux clients COM comme suit.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Les clients COM Visual Basic 6 ne peuvent pas implémenter de méthodes d'interface avec un trait de soulignement dans le nom.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, renommez les méthodes surchargées afin que les noms soient uniques.  Vous pouvez aussi rendre l'interface invisible à COM en remplaçant l'accessibilité par `internal` \(`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) ou en appliquant l'ensemble d'attributs <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> avec la valeur `false`.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente une interface qui enfreint la règle et une autre qui satisfait la règle.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Règles connexes  
 [CA1413 : Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)