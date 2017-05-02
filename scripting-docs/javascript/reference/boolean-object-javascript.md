---
title: "Boolean, objet (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "booléen (type de données), Boolean (objet)"
  - "Boolean (objet)"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean, objet (JavaScript)
Crée une valeur booléenne.  
  
## Syntaxe  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## Paramètres  
 `boolObj`  
 Obligatoire.  Nom de la variable à laquelle l'objet `Boolean` est assigné.  
  
 `boolValue`  
 Facultatif.  Valeur booléenne initiale du nouvel objet.  Si la `boolvalue` est omise ou qu'elle représente les valeurs `false`, 0, `null`, ou `NaN`, ou qu'elle représente une chaîne vide, la valeur initiale de l'objet Boolean est `false`.  Sinon, la valeur initiale est `true`.  
  
## Notes  
 L'objet de `Boolean` est un objet de wrapper pour le type de données booléen.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise implicitement l'objet `Boolean` chaque fois qu'un type de données booléen est converti en un objet de `Boolean`.  
  
 Rares sont les fois où vous instanciez explicitement l'objet de `Boolean`.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Boolean`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-boolean.md)|Spécifie la fonction qui crée une valeur booléenne.|  
|[prototype, propriété](../../javascript/reference/prototype-property-boolean.md)|Retourne une référence au prototype d'une valeur booléenne.|  
  
<a name="js56jsobjarraymeth"></a>   
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Boolean`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[toString, méthode](../../javascript/reference/tostring-method-boolean-1.md)|Retourne une représentation sous forme de chaîne d'une valeur booléenne.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-boolean.md)|Obtient une référence à la valeur booléenne.|  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]