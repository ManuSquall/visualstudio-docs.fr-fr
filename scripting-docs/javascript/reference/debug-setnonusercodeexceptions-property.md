---
title: "Debug.setNonUserCodeExceptions, propri&#233;t&#233; | Microsoft Docs"
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
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions, propri&#233;t&#233;
Détermine si les blocs try\-catch dans cette portée doivent être traités par le débogueur comme étant non gérés par l'utilisateur.  Les exceptions peuvent être classées comme levées, non gérées par l'utilisateur ou non gérées.  
  
 Si cette propriété a la valeur `true` dans une portée donnée, le débogueur peut décider d'entreprendre une action \(telle que l'arrêt\) en cas d'exceptions levées dans cette portée si le développeur souhaite s'arrêter à chaque exception non gérée par l'utilisateur.  Si cette propriété a la valeur `false`, elle a le même effet que si la propriété n'avait jamais été définie.  
  
 Pour plus d'informations sur le débogage, consultez [Présentation du débogage de script actif](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## Syntaxe  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## Exemple  
 Le code suivant illustre comment définir cette propriété.  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]