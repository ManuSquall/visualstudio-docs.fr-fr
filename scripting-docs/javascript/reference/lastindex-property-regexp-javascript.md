---
title: "lastIndex, propri&#233;t&#233; (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex (propriété)"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex, propri&#233;t&#233; (RegExp) (JavaScript)
Retourne la position du caractère où débute la prochaine correspondance trouvée dans une chaîne recherchée.  
  
## Syntaxe  
  
```  
  
RegExp.lastIndex  
```  
  
## Notes  
 L'objet associé à cette propriété est toujours l'objet `RegExp` global.  
  
 La propriété `lastIndex` est à base zéro, c'est\-à\-dire que l'index du premier caractère correspond à la valeur zéro.  Sa valeur initiale est \-1.  Sa valeur est modifiée à chaque mise en correspondance réussie.  
  
 La propriété `lastIndex` est modifiée par les méthodes `exec` et **test** de l'objet `RegExp` et par les méthodes `match`, **replace** et **split** de l'objet `String`.  
  
 Les règles suivantes s'appliquent aux valeurs de la propriété `lastIndex` :  
  
-   Si aucune correspondance n'est trouvée, la propriété `lastIndex` prend la valeur \-1.  
  
-   Si la valeur `lastIndex` est supérieure à la longueur de la chaîne, les méthodes **test** et `exec` échouent, et `lastIndex` prend la valeur \-1.  
  
-   Si la valeur `lastIndex` est égale à la longueur de la chaîne, l'expression régulière correspond si le modèle correspond à la chaîne vide.  Sinon, il n'y a pas correspondance et `lastIndex` reprend la valeur \-1.  
  
-   Sinon, `lastIndex` prend pour valeur la première position qui suit la dernière correspondance trouvée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété `lastIndex`.  Cette fonction itère une chaîne recherchée et affiche les valeurs **index** et `lastIndex` pour chaque mot de la chaîne.  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)  
  
## Voir aussi  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)