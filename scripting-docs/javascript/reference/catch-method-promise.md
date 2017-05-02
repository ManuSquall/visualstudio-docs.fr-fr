---
title: "catch, m&#233;thode (Promise) | Microsoft Docs"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# catch, m&#233;thode (Promise)
Vous permet de spécifier le travail à effectuer sur le rejet d'une promesse.  
  
## Syntaxe  
  
```  
  
promise.catch(onRejected)  
```  
  
#### Paramètres  
 `promise`  
 Obligatoire.  Objet de promesse.  
  
 `onRejected`  
 Obligatoire.  Fonction de gestionnaire d'erreurs à exécuter quand une promesse est rejetée.  
  
## Notes  
  
## Exemple  
 Dans l'exemple de code suivant, le premier appel au délai d'attente est retourné après 5 000 ms.  Dans ce code, la promesse est rejetée et la fonction de gestionnaire d'erreurs est exécutée.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]