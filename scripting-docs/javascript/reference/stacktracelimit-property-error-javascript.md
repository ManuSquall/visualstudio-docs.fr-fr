---
title: "stackTraceLimit, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Limite du suivi de la pile d'erreur (JavaScript)"
  - "pile d'erreur de JavaScript"
  - "pile d'erreur (JavaScript)"
  - "limite de la trace la pile JavaScript"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit, propri&#233;t&#233; (Error) (JavaScript)
Obtient ou définit la limite de trace de la pile, qui équivaut au nombre de frames d'erreur à afficher.  La valeur par défaut est 10.  
  
## Syntaxe  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## Notes  
 Vous pouvez attribuer à la propriété `stackTraceLimit` une valeur positive comprise entre 0 et `Infinity`.  Si la propriété `stackTraceLimit` a la valeur 0 lorsqu'une erreur est levée, aucune trace de la pile n'est affichée.  Si la propriété a une valeur négative ou non numérique, la valeur est convertie en 0.  Si la valeur de stackTraceLimit est `Infinity`, la pile entière est affichée.  Sinon, `ToUint32` est utilisé pour convertir la valeur.  
  
## Exemple  
 L'exemple suivant montre comment définir puis obtenir la limite de trace de la pile.  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## Configuration requise  
 Pris en charge dans Internet Explorer 10 et dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [description, propriété \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name, propriété \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stack, propriété \(Error\)](../../javascript/reference/stack-property-error-javascript.md)