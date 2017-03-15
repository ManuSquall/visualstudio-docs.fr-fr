---
title: "D&#233;pannage des exceptions&#160;: System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "EndOfStreamException (classe)"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IO.EndOfStreamException
Une exception <xref:System.IO.EndOfStreamException> est levée lors d'une tentative de lecture au\-delà de la fin d'un flux.  
  
## Conseils associés  
 **Vérifiez si la fin du fichier a été atteinte avant d'entamer la lecture.**  
 Utilisez la méthode <xref:System.IO.StreamReader.Peek%2A> pour vérifier la fin du fichier avant de lire à partir du flux.  
  
## Voir aussi  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Comment : lire et écrire dans un fichier de données créé récemment](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)