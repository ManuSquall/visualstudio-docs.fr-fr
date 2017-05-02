---
title: "index, propri&#233;t&#233; (RegExp) (JavaScript) | Microsoft Docs"
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
  - "index"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Index (propriété)"
  - "mise en correspondance de chaînes"
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# index, propri&#233;t&#233; (RegExp) (JavaScript)
Retourne la position du caractère où commence la première correspondance trouvée dans une chaîne recherchée.  Lecture seule.  
  
## Syntaxe  
  
```  
  
RegExp.index   
```  
  
## Notes  
 L'objet associé à cette propriété est toujours l'objet `RegExp` global.  
  
 La propriété **index** est de base zéro.  La valeur initiale de la propriété **index** est –1.  Sa valeur change chaque fois qu'une correspondance est trouvée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété **index** :  Cette fonction itère une chaîne recherchée et affiche les valeurs de `lastIndex` et **index** pour chaque mot de la chaîne.  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)  
  
## Voir aussi  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)