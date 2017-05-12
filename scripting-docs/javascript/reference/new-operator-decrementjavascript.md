---
title: "new, op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "nouvel opérateur dans JavaScript"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new, op&#233;rateur (JavaScript)
Crée un objet.  
  
## Syntaxe  
  
```  
new constructor ([arguments])   
```  
  
## Paramètres  
 `constructor`  
 Obligatoire.  Constructeur de l'objet.  Les parenthèses peuvent être omises si aucun argument n'est transmis au constructeur.  
  
 `arguments`  
 Facultatif.  Arguments passés au constructeur du nouvel objet.  
  
## Notes  
 L'opérateur `new` effectue les tâches suivantes :  
  
-   Il crée un objet sans membres.  
  
-   Il appelle le constructeur de cet objet, et passe un pointeur vers le nouvel objet créé en tant que pointeur `this`.  
  
-   Le constructeur initialise ensuite l'objet en fonction des arguments qui lui ont été passés.  
  
 Voici quelques exemples d'utilisation correcte de l'opérateur **new**.  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [function, instruction](../../javascript/reference/function-statement-javascript.md)