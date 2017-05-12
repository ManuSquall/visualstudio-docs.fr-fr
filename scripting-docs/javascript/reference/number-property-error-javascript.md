---
title: "number, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (propriété)"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number, propri&#233;t&#233; (Error) (JavaScript)
Retourne ou définit la valeur numérique associée à une erreur spécifique.  La propriété par défaut de l'objet `Error` est **number**.  
  
## Syntaxe  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## Paramètres  
 *Object*  
 Instance de l'objet `Error`.  
  
 *errorNumber*  
 Entier représentant une erreur.  
  
## Notes  
 Un numéro d'erreur est une valeur de 32 bits.  Le mot de 16 bits principal correspond au code de service et le mot secondaire au code d'erreur.  Pour déterminer le code d'erreur, utilisez l'opérateur de bits AND \(`&`\) afin de combiner la propriété number avec le nombre hexadécimal `0xFFFF`.  
  
## Exemple  
 Dans l'exemple suivant, une exception est levée et le code d'erreur dérivé du numéro d'erreur s'affiche.  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## Exemple  
 Le résultat généré par ce code est le suivant.  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [description, propriété \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name, propriété \(Error\)](../../javascript/reference/name-property-error-javascript.md)