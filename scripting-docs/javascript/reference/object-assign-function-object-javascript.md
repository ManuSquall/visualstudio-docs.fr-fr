---
title: "Object.assign, fonction (Object) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Object.assign, fonction (Object) (JavaScript)
Copie les valeurs d'un ou de plusieurs objets sources dans un objet cible.  
  
## Syntaxe  
  
```  
Object.assign(target, ...sources );  
```  
  
#### Paramètres  
 `target`  
 Obligatoire.  Objet dans lequel les propriétés énumérables sont copiées.  
  
 `...sources`  
 Obligatoire.  Un ou plusieurs objets à partir desquels les propriétés énumérables sont copiées.  
  
## Exceptions  
 Cette fonction génère une erreur `TypeError` dans le cas d'une erreur d'assignation, qui met fin à l'opération de copie.  Une exception `TypeError` est levée si une propriété cible n'est pas accessible en écriture.  
  
## Notes  
 Cette fonction retourne l'objet cible.  Seules les propriétés *enumerable own* sont copiées de l'objet source vers l'objet cible.  Vous pouvez utiliser cette fonction pour fusionner ou cloner des objets.  
  
 Les sources `null` ou `undefined` sont traitées comme des objets vides et n'apportent rien à l'objet cible.  
  
## Exemple  
 L'exemple de code suivant montre comment fusionner un objet avec `Object.assign`.  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## Exemple  
 L'exemple suivant montre comment cloner un objet avec `Object.assign`.  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]