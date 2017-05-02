---
title: "Exception lev&#233;e mais non intercept&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Exception lev&#233;e mais non intercept&#233;e
L'instruction `throw` que vous avez inclue dans votre code n'a pas été placée dans un bloc **try**, ou le bloc **catch** n'y était pas associé afin d'intercepter l'erreur.  Les exceptions sont levées de l'intérieur du bloc **try** par l'instruction **throw**, et interceptées à l'extérieur du bloc **try** par une instruction **catch**.  
  
### Pour corriger cette erreur  
  
-   Insérez le code qui lève une exception dans un bloc **try** , et assurez\-vous qu'il soit associé à un bloc **catch**.  
  
-   Assurez\-vous que l'instruction catch attend la forme correcte de l'exception.  
  
-   Si l'exception est levée à nouveau, assurez\-vous qu'il existe une autre instruction catch qui lui correspond.  
  
## Voir aussi  
 [Error, objet](../../javascript/reference/error-object-javascript.md)   
 [Instruction throw](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)