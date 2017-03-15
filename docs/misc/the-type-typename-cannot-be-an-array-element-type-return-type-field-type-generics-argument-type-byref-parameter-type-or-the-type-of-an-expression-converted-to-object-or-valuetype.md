---
title: "Le type &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre un type d’&#233;l&#233;ment de tableau, type de retour, type de champ, type d’argument g&#233;n&#233;rique, type de param&#232;tre &#39;ByRef&#39; ni le type d’une expression convertie en &#39;Object&#39; ou &#39;ValueType&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre un type d’&#233;l&#233;ment de tableau, type de retour, type de champ, type d’argument g&#233;n&#233;rique, type de param&#232;tre &#39;ByRef&#39; ni le type d’une expression convertie en &#39;Object&#39; ou &#39;ValueType&#39;
Une expression déclare une variable, un paramètre de procédure, un paramètre de type, un retour de fonction ou un tableau comme étant d’un type restreint.  
  
 Le Common Language Runtime \(CLR\) expose certains types uniquement pour une prise en charge spéciale des langages, et ils ne doivent pas servir en tant que types de données dans votre application. Ces types incluent les structures <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle> et <xref:System.TypedReference>.  
  
 **ID d’erreur :** BC31396  
  
### Pour corriger cette erreur  
  
-   N’utilisez pas la structure restreinte comme type de données déclaré.  
  
## Voir aussi  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>