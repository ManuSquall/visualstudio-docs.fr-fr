---
title: "endsWith, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# endsWith, m&#233;thode (String) (JavaScript)
Retourne une valeur qui indique si une chaîne ou sous\-chaîne se termine par une autre chaîne spécifiée.  
  
## Syntaxe  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### Paramètres  
 `stringObj`  
 Obligatoire.  Objet String pour la recherche.  
  
 `str`  
 Obligatoire.  Chaîne recherchée.  
  
 `position`  
 Facultatif.  Position du premier caractère pour la recherche dans l'objet String, en commençant à 0.  
  
## Valeur de retour  
 Si la chaîne commençant à `position` se termine par la chaîne recherchée, la méthode `endsWith` retourne `true` ; sinon, elle retourne `false`.  
  
## Exceptions  
 Si `str` est un `RegExp`, une `TypeError` est générée.  
  
## Notes  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]