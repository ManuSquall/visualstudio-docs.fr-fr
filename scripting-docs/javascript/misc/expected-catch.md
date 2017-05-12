---
title: "&#39;catch&#39; attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &#39;catch&#39; attendu
Vous avez utilisé le bloc **try** de gestion des exceptions, mais n'avez pas écrit l'instruction **catch** associée.  Le mécanisme de gestion des exceptions nécessite que le code qui peut échouer, ainsi que le code qui ne doit pas s'exécuter si une exception est levée, soient encapsulés dans un bloc **try**.  Les exceptions sont levées depuis le bloc **try** à l'aide de l'instruction **throw**, puis interceptées en dehors du bloc **try** avec une ou plusieurs instructions **catch**.  
  
### Pour corriger cette erreur  
  
-   Ajoutez le bloc **catch** associé.  
  
-   Utilisez un bloc **finally** au lieu d'un bloc **catch**.  
  
## Voir aussi  
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error, objet](../../javascript/reference/error-object-javascript.md)