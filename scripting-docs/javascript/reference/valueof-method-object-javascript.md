---
title: "valueOf, m&#233;thode (Object) (JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf (méthode)"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf, m&#233;thode (Object) (JavaScript)
Retourne la valeur primitive de l'objet spécifié.  
  
## Syntaxe  
  
```  
  
object.valueOf( )  
```  
  
## Notes  
 La référence `object` requise est un objet intrinsèque de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 La méthode `valueOf` est définie de façon différente pour chaque objet intrinsèque de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
|Objet|Valeur de retour|  
|-----------|----------------------|  
|Array|Retourne l'instance de tableau.|  
|Boolean|Valeur booléenne.|  
|Date|Valeur horaire stockée, exprimée en millisecondes écoulées depuis le 1er janvier 1970 à minuit \(temps universel\).|  
|Fonction|La fonction elle\-même.|  
|Number|Valeur numérique.|  
|Objet|L'objet lui\-même.  Il s'agit d'une valeur par défaut.|  
|Chaîne|Valeur de chaîne.|  
  
 Les objets **Math** et `Error` n'ont pas de méthode `valueOf`.  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **S'applique à** : [Objet Array](../../javascript/reference/array-object-javascript.md)&#124; [Boolean, objet](../../javascript/reference/boolean-object-javascript.md)&#124; [Date, objet](../../javascript/reference/date-object-javascript.md)&#124; [Objet de function](../../javascript/reference/function-object-javascript.md)&#124; [Number, objet](../../javascript/reference/number-object-javascript.md)&#124; [Object, objet](../../javascript/reference/object-object-javascript.md)&#124; [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [toString, méthode \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)