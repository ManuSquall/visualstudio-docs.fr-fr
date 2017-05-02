---
title: "Labeled, instruction (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (instruction)"
  - "identificateurs, instructions"
  - "labeled (instruction)"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Labeled, instruction (JavaScript)
Fournit un identificateur pour une instruction.  
  
## Syntaxe  
  
```  
  
      label :  
   statements   
```  
  
## Paramètres  
 *label*  
 Obligatoire.  Identificateur unique utilisé pour faire référence à l'instruction étiquetée.  
  
 `statements`  
 Facultatif.  Une ou plusieurs instructions associées à *label*.  
  
## Notes  
 Les étiquettes permettent aux instructions **break** et **continue** de spécifier l'instruction à laquelle les instructions **break** et **continue** s'appliquent.  
  
## Exemple  
 Dans le code suivant, l'instruction **continue** fait référence à la boucle **for** précédée de l'instruction `Inner:`.  Lorsque `j` est égal à 24, l'instruction **continue** force la boucle **for** à passer à l'itération suivante.  Les nombres 21 à 23 et 25 à 30 s'impriment sur chaque ligne.  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)