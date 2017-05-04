---
title: "Promise.all, fonction (Promise) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.all, fonction (Promise)
Joint plusieurs promesses et retourne une valeur uniquement quand toutes les promesses spécifiées ont été réalisées ou rejetées.  
  
## Syntaxe  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### Paramètres  
 `func1`  
 Obligatoire.  Fonction qui retourne une promesse.  
  
 `func2`  
 Obligatoire.  Fonction qui retourne une promesse.  
  
 `funcN`  
 Facultatif.  Une ou plusieurs fonctions qui retournent une promesse.  
  
## Notes  
 Le résultat retourné est un tableau de valeurs retournées par les promesses réalisées.  Si l'une des promesses jointes est rejetée, `Promise.all` en retourne immédiatement la raison \(toutes les autres valeurs de retour sont ignorées\).  
  
## Exemple  
 Dans ce code, le premier appel au délai d'attente est retourné après 5 000 ms.  Le gestionnaire d'achèvement appelle `Promise.all`, qui retourne une valeur uniquement quand les deux appels au délai d'attente sont réalisés ou rejetés.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)