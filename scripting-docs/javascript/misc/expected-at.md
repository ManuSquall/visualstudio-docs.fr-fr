---
title: "&#39;@&#39; attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# &#39;@&#39; attendu
Vous avez essayé de créer une variable à utiliser avec des instructions de compilation conditionnelle à l'aide de l'instruction `@set`, mais n'avez pas placé de symbole « **@** » avant le nom de variable.  
  
### Pour corriger cette erreur  
  
-   Ajoutez un symbole « **@** » immédiatement avant le nom de variable.  Par exemple :  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## Voir aussi  
 [@set, instruction](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)