---
title: "Aucune m&#233;thode accessible &#39;&lt;nom_proc&#233;dure&gt;&#39; n’a de signature compatible avec le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;:&lt;liste_sous_erreurs&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aucune m&#233;thode accessible &#39;&lt;nom_proc&#233;dure&gt;&#39; n’a de signature compatible avec le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;:&lt;liste_sous_erreurs&gt;
Une instruction d’assignation assigne l’adresse d’une procédure à une variable de délégué, mais le compilateur ne peut pas trouver une version de la procédure avec une signature correspondante.  
  
 Quand le code utilise l’adresse d’une procédure, le compilateur tente de trouver une version de cette procédure avec une liste de paramètres qui correspond à celle du délégué. Si la procédure est définie dans plusieurs versions surchargées, le compilateur tente de trouver une version unique avec une signature correspondante. Pour plus d'informations, consultez [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Si le compilateur ne peut pas trouver de version de la procédure avec une signature correspondante, il génère cette erreur. Cela peut se produire si, par exemple, la procédure ou le délégué est générique et qu’un argument de type qui lui est passé lui attribue une signature qui ne correspond pas à l’autre signature.  
  
 **ID d’erreur :** BC30950  
  
### Pour corriger cette erreur  
  
1.  Redéfinissez la procédure ou le délégué pour que leurs listes de paramètres correspondent.  
  
     ou  
  
     Définissez un nouveau délégué avec une liste de paramètres qui correspond à celle de la procédure, ou définissez une nouvelle procédure avec une liste de paramètres qui correspond à celle du délégué.  
  
2.  Si la procédure ou le délégué est générique, passez\-lui un argument de type qui engendre la mise en correspondance des deux signatures.  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)