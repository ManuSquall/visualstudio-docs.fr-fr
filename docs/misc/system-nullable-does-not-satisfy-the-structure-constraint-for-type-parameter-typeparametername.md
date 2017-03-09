---
title: "&#39;System.Nullable&#39; ne satisfait pas la contrainte &#39;Structure&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Nullable&#39; ne satisfait pas la contrainte &#39;Structure&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;
Un type générique est appelé en passant un argument de type <xref:System.Nullable%601> à un paramètre de type avec une contrainte `Structure`.  
  
 Le Common Language Runtime \(CLR\) interdit spécifiquement la structure <xref:System.Nullable%601> en tant qu’argument de type à lui\-même. Bien qu’il s’agisse d’une structure et qu’elle pourrait satisfaire une contrainte `Structure`, son utilisation récursive peut entraîner des constructions maladroites telles que `Nullable(Of Nullable(Of Nullable))`.  
  
 **ID d’erreur :** BC32115  
  
### Pour corriger cette erreur  
  
-   Supprimez la contrainte `Structure` du paramètre de type, ou remplacez l’argument de type par un type valeur autre que <xref:System.Nullable%601>.  
  
## Voir aussi  
 <xref:System.Nullable%601>   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)