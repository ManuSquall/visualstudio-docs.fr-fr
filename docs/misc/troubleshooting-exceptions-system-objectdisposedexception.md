---
title: "D&#233;pannage des exceptions&#160;: System.ObjectDisposedException | Microsoft Docs"
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
  - "ObjectDisposedException (classe), résolution des problèmes"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ObjectDisposedException
Une exception <xref:System.ObjectDisposedException> est levée lorsqu'une opération est tentée sur un objet supprimé, tel qu'un flux fermé ou une clé fermée du Registre.  
  
## Conseils associés  
 **Assurez\-vous que vous n'avez pas libéré une ressource avant de l'utiliser.**  
 Par exemple, si vous tentez de manipuler un flux, assurez\-vous qu'il n'a pas été précédemment fermé.  
  
## Voir aussi  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)