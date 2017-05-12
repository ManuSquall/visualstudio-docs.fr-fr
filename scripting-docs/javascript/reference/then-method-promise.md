---
title: "then, m&#233;thode (Promise) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# then, m&#233;thode (Promise)
Vous permet de spécifier le travail à effectuer sur la réalisation d'une promesse.  
  
## Syntaxe  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### Paramètres  
 `promise`  
 Obligatoire.  Objet de promesse.  
  
 `onCompleted`  
 Obligatoire.  Fonction de gestionnaire des réalisations à exécuter quand la promesse est correctement réalisée.  
  
 `onRejected`  
 Facultatif.  Fonction de gestionnaire d'erreurs à exécuter quand la promesse est rejetée.  
  
## Notes  
 Une promesse doit être réalisée avec une valeur ou rejetée avec une raison.  La méthode `then` de l'objet Promise s'exécute quand la promesse est réalisée ou rejetée, selon ce qui se produit en premier.  Si la promesse est réalisée avec succès, la fonction de gestionnaire des réalisations de la méthode `then` s'exécute.  Si la promesse est rejetée, la fonction de gestionnaire d'erreurs de la méthode `then` \(ou la méthode `catch` \) s'exécute.  
  
## Exemple  
 L'exemple suivant montre comment appeler une fonction \(`timeout`\) qui retourne une promesse.  Le gestionnaire des réalisations de la méthode `then` s'exécute après l'expiration du délai d'attente de 5 000 ms.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)