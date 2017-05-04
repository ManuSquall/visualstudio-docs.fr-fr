---
title: "message, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message (propriété)"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message, propri&#233;t&#233; (Error) (JavaScript)
Retourne une chaîne de message d'erreur.  
  
## Syntaxe  
  
```  
  
errorObj.message  
```  
  
## Paramètres  
 `errorObj`  
 Obligatoire.  Instance d'un objet `Error`.  
  
## Notes  
 La propriété `message` retourne une chaîne contenant un message d'erreur associé à une erreur spécifique.  
  
 Les propriétés `description` et `message` fournissent la même fonctionnalité.  La propriété `description` fournit une compatibilité descendante ; la propriété `message` est conforme à la norme ECMA.  
  
## Exemple  
 L'exemple suivant provoque la levée d'une exception TypeError et l'affichage du message d'erreur et le nom de celle\-ci.  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Exemple  
 Le résultat généré par ce code est le suivant.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [description, propriété \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [name, propriété \(Error\)](../../javascript/reference/name-property-error-javascript.md)