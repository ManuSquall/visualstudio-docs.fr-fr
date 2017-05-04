---
title: "JSON, objet (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON (objet)"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# JSON, objet (JavaScript)
Objet intrinsèque qui fournit des fonctions de conversion de valeurs [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] au format JSON \(JavaScript Object Notation\) et à partir de ce dernier.  La fonction `JSON.stringify` sérialise une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en texte JSON.  La fonction `JSON.parse` désérialise du texte JSON pour produire une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Syntaxe  
  
```  
  
JSON.[method]  
  
```  
  
## Paramètres  
 `Method`  
 Requis.  Nom de l'une des méthodes de l'objet `JSON`.  
  
## Notes  
 Vous ne pouvez pas créer un objet `JSON` à l'aide de l'opérateur `new`.  Une erreur se produit si vous tentez d'effectuer cette opération.  Toutefois, vous pouvez remplacer ou modifier l'objet `JSON`.  
  
 Le moteur de script crée l'objet `JSON` lorsque le moteur est chargé.  Ses méthodes sont accessibles à votre script à tout moment.  
  
 Pour utiliser l'objet `JSON` intrinsèque, veillez à ne pas le remplacer par un autre objet `JSON` défini dans votre script.  Vous devrez peut\-être modifier les instructions de script existantes qui détectent la présence d'un objet `JSON` car ces instructions évaluent différemment.  Cela est illustré par l'exemple suivant.  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 Dans l'exemple précédent, `!this.JSON` prend la valeur false dans [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)].  Par conséquent, le code contenu dans l'instruction `if` ne s'exécute pas.  
  
## Fonctions  
 [JSON.parse, fonction](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify, fonction](../../javascript/reference/json-stringify-function-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Voir aussi  
 [toJSON, méthode \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript, objets](../../javascript/reference/javascript-objects.md)   
 [Application d'exemple avec le modèle Hub \(Windows Store\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)