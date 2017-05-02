---
title: "ArrayBuffer.isView, fonction (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView, fonction (ArrayBuffer)
Détermine si un objet fournit une vue de la mémoire tampon.  
  
## Syntaxe  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### Paramètres  
 `object`  
 Requis.  Objet à tester.  
  
## Valeur de retour  
 `true` si l'une ou l'autre des affirmations suivantes est vraie :  
  
-   `object` est un objet `DataView`.  
  
-   `object` es un tableau typé.  
  
 Dans le cas contraire, la méthode retourne `false`.  
  
## Notes  
  
## Exemple  
 L'exemple suivant montre l'utilisation de la fonction `isView` pour tester un tableau typé et un objet `DataView`.  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Voir aussi  
 [Uint8ClampedArray, objet](../../javascript/reference/uint8clampedarray-object-javascript.md)