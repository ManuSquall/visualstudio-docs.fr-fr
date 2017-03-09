---
title: "D&#233;pannage des exceptions&#160;: System.Data.ReadOnlyException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "ReadOnlyException (classe)"
ms.assetid: 1ac5da38-c5af-4fec-8fe1-1b9dd5069e59
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.ReadOnlyException
Une exception <xref:System.Data.ReadOnlyException> est levée lors d'une tentative de modification de la valeur d'une colonne de données en lecture seule.  
  
## Conseils associés  
 **Faites passer la colonne en lecture\/écriture.**  
 Cette exception est levée si vous tentez de modifier une valeur dans une colonne de données en lecture seule. Pour plus d'informations, consultez <xref:System.Data.DataColumn>.  
  
 **Assurez\-vous que vous modifiez les données dans la colonne appropriée.**  
 Cette exception est levée si vous tentez de modifier une valeur dans une colonne de données en lecture seule. Pour plus d'informations, consultez <xref:System.Data.DataColumn>.  
  
## Voir aussi  
 <xref:System.Data.ReadOnlyException>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)