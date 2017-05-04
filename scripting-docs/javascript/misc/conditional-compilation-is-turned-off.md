---
title: "La compilation conditionnelle est d&#233;sactiv&#233;e | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# La compilation conditionnelle est d&#233;sactiv&#233;e
Vous avez tenté d'utiliser une variable de compilation conditionnelle sans activer la compilation conditionnelle au préalable.  L'activation de la compilation conditionnelle indique au compilateur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] d'interpréter les identificateurs commençant par @ comme des variables de compilation conditionnelle.  Pour cela, commencez votre code conditionnel avec l'instruction suivante :  
  
```  
/*@cc_on @*/  
```  
  
### Pour corriger cette erreur  
  
-   Ajoutez l'instruction suivante au début de votre code conditionnel :  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on, instruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if, instruction](../../javascript/reference/at-if-statement-javascript.md)   
 [@set, instruction](../../javascript/reference/at-set-statement-javascript.md)