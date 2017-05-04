---
title: "Fonction attendue | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Fonction attendue
Vous avez tenté d'appeler l'une des méthodes **Function prototype** sur un objet qui n'était pas un objet `Function`, ou vous avez utilisé un objet dans un contexte d'appel de fonction.  Par exemple, le code suivant génère cette erreur car **example**  n'est pas une fonction.  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### Pour corriger cette erreur  
  
-   Appelez uniquement les méthodes **Function prototype** sur des objets `Function`.  
  
-   Assurez\-vous de n'utiliser l'opérateur d'appel de fonction `()` que pour appeler des fonctions.  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [prototype, propriété \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)