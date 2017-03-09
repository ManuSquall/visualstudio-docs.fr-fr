---
title: "D&#233;pannage des exceptions&#160;: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException (exception)"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException (exception)"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
Exception levée lorsque la seconde instance d'une application à instance unique n'a pas pu se connecter à l'instance d'origine.  
  
## Notes  
 Ce problème peut avoir plusieurs causes :  
  
-   L'instance d'origine a cessé de répondre.  
  
-   L'application n'a pas l'autorisation de créer des objets du noyau.  
  
     Le nom de base des objets du noyau est une concaténation entre le GUID de l'assembly, le numéro de la version principale et le numéro de la version secondaire. Par exemple, le nom de base pourrait être 3639f15d\-9547\-43da\-8145\-60da347829915.1.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)