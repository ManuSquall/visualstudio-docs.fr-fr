---
title: "toString, m&#233;thode (Number) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString, m&#233;thode (Number)
Retourne une représentation sous forme de chaîne d'un nombre.  
  
## Syntaxe  
  
```  
  
number.toString()  
```  
  
## Paramètres  
 `number`  
 Obligatoire.  Nombre à représenter sous forme de chaîne.  
  
## Valeur de retour  
 Représentation sous forme de chaîne du nombre.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode **toString** avec un nombre.  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]