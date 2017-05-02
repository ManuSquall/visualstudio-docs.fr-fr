---
title: "stack, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "pile d'erreur (JavaScript)"
  - "pile d'erreur de JavaScript"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# stack, propri&#233;t&#233; (Error) (JavaScript)
Obtient ou définit la pile d'erreur sous forme de chaîne qui contient les images de frame de pile.  
  
## Syntaxe  
  
```  
  
object  
.stack   
```  
  
## Notes  
 La propriété `stack` prend la valeur `undefined` quand l'erreur est construite et obtient les informations de trace quand l'erreur est levée.  Si une erreur se produit plusieurs fois, la propriété `stack` est mise à jour chaque fois que l'erreur est levée.  
  
 Les frames de pile sont affichés au format suivant : à NomFonction \(\<nom\_complet\/URL\>:\<numéro\_ligne\>:\<numéro\_colonne\>\)  
  
 Si vous créez votre propre objet d'erreur et que vous affectez une valeur au frame de pile, la valeur n'est pas remplacée quand l'erreur est levée.  
  
 La propriété `stack` n'affiche pas les fonctions inline dans ses frames.  Elle affiche uniquement la pile physique.  
  
## Exemple  
 L'exemple suivant montre comment obtenir la pile quand vous interceptez une erreur.  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Exemple  
 L'exemple suivant montre comment définir puis obtenir la pile.  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [description, propriété \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name, propriété \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit, propriété \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)