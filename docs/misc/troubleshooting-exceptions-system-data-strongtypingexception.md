---
title: "D&#233;pannage des exceptions&#160;: System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException (classe)"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.StrongTypingException
Une exception <xref:System.Data.StrongTypingException> se produit l'utilisateur accède à une valeur <xref:System.DBNull> dans un <xref:System.Data.DataTable.DataSet%2A> fortement typé.  
  
## Conseils associés  
 **Ajoutez la gestion de l'erreur StrongTypingException.**  
 Placez le code qui accède au <xref:System.Data.DataTable.DataSet%2A> dans un bloc `Try…Catch` et interceptez <xref:System.Data.StrongTypingException>.  
  
## Voir aussi  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)