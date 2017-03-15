---
title: "D&#233;pannage des exceptions&#160;: System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException (exception)"
  - "AccessViolationException (classe)"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.AccessViolationException
Une <xref:System.AccessViolationException> est levée lors d'une tentative de lecture ou d'écriture de données dans une mémoire protégée.  
  
## Conseils associés  
 Assurez\-vous que la mémoire à laquelle vous tentez d'accéder a été allouée.  
 La gestion automatique de la mémoire est un des services que le Common Language Runtime fournit. Vous pouvez souhaiter passer à du code managé pour tirer parti de ce service. Pour plus d'informations, consultez [Gestion automatique de la mémoire](../Topic/Automatic%20Memory%20Management.md).  
  
 Assurez\-vous que la mémoire à laquelle vous tentez d'accéder n'a pas été endommagée.  
 Si plusieurs opérations de lecture et d'écriture ont été effectuées par le biais de pointeurs erronés, la mémoire peut être endommagée.  
  
### Notes  
 Une violation d'accès se produit en code non managé ou unsafe lorsqu'il tente de lire ou d'écrire dans une mémoire qui n'a pas été allouée, ou à laquelle il n'a pas accès. Toutes les opérations de lecture ou d'écriture avec des pointeurs erronés ne provoquent pas des violations d'accès, une violation d'accès indique donc habituellement que plusieurs opérations de lecture ou d'écriture ont été exécutées par le biais de pointeurs erronés et que cette mémoire est peut\-être endommagée.  
  
 En code managé, toutes les références sont valides ou null. Toute opération qui tente de référencer une référence null dans du code vérifiable lève <xref:System.NullReferenceException>.  
  
 Une violation d'accès qui se produit dans du code managé unsafe peut être exprimée comme une <xref:System.NullReferenceException> ou une <xref:System.AccessViolationException>, selon la plateforme.  
  
 Les violations d'accès dans du code non managé qui se propagent dans du code managé sont toujours encapsulées dans une <xref:System.AccessViolationException>.  
  
## Voir aussi  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Gestion de la mémoire : exemples](../Topic/Memory%20Management:%20Examples.md)   
 [Gestion automatique de la mémoire](../Topic/Automatic%20Memory%20Management.md)