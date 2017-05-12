---
title: "Objet date attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Objet date attendu
Vous avez tenté d'appeler la méthode **Data.prototype.toString** ou **Data.prototype.valueOf** sur un objet qui n'est pas de type `Date`.  L'objet de ce type d'appel doit être de type `Date`.  Par exemple :  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### Pour corriger cette erreur  
  
-   Les méthodes **Date.prototype.toString** ou **Date.prototype.valueOf** ne doivent être appelées que sur des objets de type `Date`.  
  
## Voir aussi  
 [Date, objet](../../javascript/reference/date-object-javascript.md)   
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md)