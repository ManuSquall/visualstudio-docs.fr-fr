---
title: "constructor, propri&#233;t&#233; (Boolean) | Microsoft Docs"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor, propri&#233;t&#233; (Boolean)
Spécifie la fonction qui crée une valeur booléenne.  
  
## Syntaxe  
  
```  
  
boolean.constructor([[value])  
```  
  
#### Paramètres  
 `boolean`  
 Nom de la valeur booléenne.  
  
 `value`  
 Facultatif.  Spécifie la valeur de la valeur booléenne.  Cela peut être les nombres 1 ou 0, ou les chaînes « true » ou « false ».  
  
## Notes  
 La propriété `constructor` contient une référence à la fonction qui construit des instances de l'objet Boolean.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]