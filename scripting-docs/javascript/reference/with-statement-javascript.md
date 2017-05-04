---
title: "with, instruction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With (instruction)"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with, instruction (JavaScript)
Définit l'objet par défaut d'une instruction.  
  
## Syntaxe  
  
```  
with (object) {  
    statements  
}   
```  
  
## Paramètres  
 `object`  
 Objet par défaut.  
  
 `statements`  
 Une ou plusieurs instructions pour lesquelles `object` est l'objet par défaut.  
  
## Notes  
 L'instruction `with` est généralement utilisée pour diminuer la quantité de code à écrire dans certaines situations.  
  
> [!WARNING]
>  L'utilisation de `with` n'est pas autorisée en mode strict.  L'utilisation de `with` peut rendre le code plus difficile à lire et à déboguer et doit généralement être évitée.  
  
## Exemple  
 Dans cet exemple, l'objet `Math` est utilisé de façon répétée :  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## Exemple  
 Si vous réécrivez l'exemple pour utiliser l'instruction `with`, votre code devient plus succinct :  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [this, instruction](../../javascript/reference/this-statement-javascript.md)