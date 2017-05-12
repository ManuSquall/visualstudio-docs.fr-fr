---
title: "name, propri&#233;t&#233; (Error) (JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Nom de la propriété"
  - "name (propriété), nom de l'erreur"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name, propri&#233;t&#233; (Error) (JavaScript)
Retourne le nom d'une erreur.  
  
## Syntaxe  
  
```  
  
errorObj.  
name  
  
```  
  
## Paramètres  
 `errorObj`  
 Obligatoire.  Instance d'un objet `Error`.  
  
## Notes  
 La propriété **name** retourne le nom ou le type d'exception d'une erreur.  Lorsqu'une erreur d'exécution se produit, la propriété name se voit attribuer l'un des types d'exceptions natives suivants :  
  
|Type d'exception|Signification|  
|----------------------|-------------------|  
|ConversionError|Cette erreur se produit à chaque tentative de conversion d'un objet en un élément dans lequel il ne peut être converti.|  
|RangeError|Cette erreur se produit lorsqu'une fonction est spécifiée avec un argument qui dépasse sa plage autorisée.  Elle se produit, par exemple, si vous tentez de construire un objet `Array` avec une longueur définie par une valeur autre qu'un entier positif.|  
|ReferenceError|Cette erreur se produit lorsqu'une référence non valide est détectée.  Elle se produit, par exemple, lorsque la référence attendue a la valeur `null`.|  
|RegExpError|Cette erreur se produit en présence d'une erreur de compilation avec une expression régulière.  Cependant, une fois que l'expression régulière est compilée, l'erreur ne peut plus se produire.  C'est le cas, par exemple, lorsqu'une expression régulière est déclarée avec un modèle comportant une syntaxe non valide, ou avec des indicateurs autres que **i**, **g** ou **m**, ou si le même indicateur est défini plusieurs fois.|  
|SyntaxError|Cette erreur se produit lorsque le texte source est analysé et que sa syntaxe est incorrecte.  C'est le cas, par exemple, si la fonction `eval` est appelée à l'aide d'un argument de programmation non valide.|  
|TypeError|Cette erreur se produit lorsque le type réel d'opérande ne correspond pas au type attendu.  C'est le cas, par exemple, lors d'un appel de fonction effectué sur un élément qui n'est pas un objet ou qui ne prend pas en charge l'appel.|  
|URIError|Cette erreur se produit lorsqu'un URI non conforme est détecté.  Elle se produit, par exemple, lorsqu'un caractère non conforme est trouvé dans une chaîne en cours d'encodage ou de décodage.|  
  
## Exemple  
 L'exemple suivant provoque la levée d'une exception TypeError et l'affichage du message d'erreur et le nom de celle\-ci.  
  
```javascript  
try  
{  
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
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Error, objet](../../javascript/reference/error-object-javascript.md)  
  
## Voir aussi  
 [description, propriété \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [number, propriété \(Error\)](../../javascript/reference/number-property-error-javascript.md)