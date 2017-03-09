---
title: "D&#233;pannage des exceptions&#160;: System.Exception | Microsoft Docs"
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
  - "System.Exception (exception)"
  - "classes de base, exceptions"
  - "exceptions, classe de base"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Exception
Représente les erreurs qui se produisent lors de l'exécution de l'application. Il s'agit de la classe de base de toutes les exceptions.  
  
## Conseils associés  
 **Pour plus d'informations, consultez la propriété InnerException.**  
 Pour résoudre l'erreur, vous pouvez avoir besoin d'informations relatives à l'exception interne \(ou antérieure\) qui a abouti à l'exception actuelle. La propriété <xref:System.Exception.InnerException%2A> de l'exception actuelle contient l'exception interne. Vous pouvez utiliser le lien **Afficher les détails** dans la boîte de dialogue **Assistant Exception** pour accéder à la propriété <xref:System.Exception.InnerException%2A>.  
  
 **Désactivez temporairement le débogage « Uniquement mon code ».**  
 L'exception s'est peut\-être produite dans du code que vous n'avez pas écrit. Pour déboguer ce code, vous devrez peut\-être désactiver le débogage « Uniquement mon code ». Pour plus d'informations, consultez [Général, Débogage, boîte de dialogue Options](../debugger/general-debugging-options-dialog-box.md).  
  
## Voir aussi  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Comment : arrêter l'exécution lorsqu'une exception est levée](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [Général, Débogage, boîte de dialogue Options](../debugger/general-debugging-options-dialog-box.md)