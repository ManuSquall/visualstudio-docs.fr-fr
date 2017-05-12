---
title: "Objet &#233;num&#233;rateur attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Objet &#233;num&#233;rateur attendu
Vous avez tenté d'appeler la méthode **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** ou **Enumerator.prototype.moveNext** sur un objet d'un type autre que `Enumerator`.  L'objet de ce type d'appel doit être de type `Enumerator`.  Voici un exemple de code qui ne respecte pas cette règle :  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### Pour corriger cette erreur  
  
-   Appelez uniquement les méthodes **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst** ou **Enumerator.prototype.moveNext** sur les objets de type `Enumerator`.  Pour déterminer si votre objet est un objet `Enumerator`, utilisez ce qui suit :  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## Voir aussi  
 [Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)