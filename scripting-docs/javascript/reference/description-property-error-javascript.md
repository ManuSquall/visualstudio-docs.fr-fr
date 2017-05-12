---
title: "description, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description (propriété)"
  - "gestion des erreurs, erreur (description)"
  - "erreurs, description"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description, propri&#233;t&#233; (Error) (JavaScript)
Retourne ou définit la chaîne descriptive associée à une erreur spécifique.  
  
## Syntaxe  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## Paramètres  
 *object*  
 Obligatoire.  Toute instance d'un objet `Error`.  
  
 `stringExpression`  
 Facultatif.  Expression de chaîne contenant une description de l'erreur.  
  
## Notes  
 La propriété **description** contient la chaîne de message d'erreur associée à une erreur spécifique.  Utilisez la valeur contenue dans cette propriété pour avertir un utilisateur d'une erreur.  
  
 Les propriétés **description** et **message** offrent les mêmes fonctionnalités ; la propriété **description** assure la compatibilité descendante ; la propriété **message** respecte la norme ECMA.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété **description**.  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [number, propriété \(Error\)](../../javascript/reference/number-property-error-javascript.md)   
 [message, propriété \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name, propriété \(Error\)](../../javascript/reference/name-property-error-javascript.md)