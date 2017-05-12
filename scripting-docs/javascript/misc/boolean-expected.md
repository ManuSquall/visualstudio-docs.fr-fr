---
title: "Bool&#233;en attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bool&#233;en attendu
Vous avez tenté d'appeler la méthode **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** sur un objet d'un type autre que `Boolean`.  L'objet de ce type d'appel doit être de type `Boolean`.  Par exemple :  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### Pour corriger cette erreur  
  
-   Appelez les méthodes **Boolean.prototype.toString** et **Boolean.prototype.valueOf** uniquement sur des objets de type **Boolean.**  
  
## Voir aussi  
 [Boolean, objet](../../javascript/reference/boolean-object-javascript.md)   
 [Types de données](../../javascript/data-types-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Copie, transmission et comparaison de données](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)