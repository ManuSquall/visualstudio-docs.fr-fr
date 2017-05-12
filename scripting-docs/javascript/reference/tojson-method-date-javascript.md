---
title: "toJSON, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toJSON (méthode)"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON, m&#233;thode (Date) (JavaScript)
Utilisé par la méthode [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) pour activer la transformation des données d'un objet pour la sérialisation JSON \(JavaScript Object Notation\).  
  
## Syntaxe  
  
```  
  
objectname.toJSON()  
```  
  
## Paramètres  
 `objectname`  
 Obligatoire.  Un objet pour lequel une sérialisation JSON est souhaitée.  
  
## Notes  
 La méthode `toJSON` est utilisée par la fonction `JSON.stringify`.  `JSON.stringify` sérialise une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en texte JSON.  Si une méthode `toJSON` est fournie à `JSON.stringify`, la méthode `toJSON` est appelée lorsque `JSON.stringify` est appelé.  
  
 La méthode `toJSON` est un membre intégré de l'objet [Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Elle retourne une chaîne de date au format ISO pour le fuseau horaire UTC \(désigné par le suffixe Z\).  
  
 Vous pouvez substituer la méthode `toJSON` du type `Date`, ou définir une méthode `toJSON` pour d'autres types d'objets afin de réaliser la transformation des données d'un type d'objet spécifique avant la sérialisation JSON.  
  
## Exemple  
 L'exemple suivant utilise la méthode `toJSON` pour sérialiser des valeurs de membre chaîne en majuscules.  La méthode `toJSON` est appelée lorsque `JSON.stringify` est appelé.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `toJSON` qui correspond à un membre intégré de l'objet [Date](../../javascript/reference/date-object-javascript.md).  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## Configuration requise  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **S'applique à :** [Objet Date](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [JSON, objet](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse, fonction](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify, fonction](../../javascript/reference/json-stringify-function-javascript.md)   
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)