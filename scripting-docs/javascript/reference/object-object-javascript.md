---
title: "Object, objet (JavaScript) | Microsoft Docs"
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
  - "object"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object (objet)"
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Object, objet (JavaScript)
Fournit des fonctionnalités communes à tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Syntaxe  
  
```  
  
obj  
 = new Object([value])   
```  
  
## Paramètres  
 `obj`  
 Obligatoire.  Nom de la variable à laquelle l'objet `Object` est assigné.  
  
 *valeur*  
 Facultatif.  N'importe quel type de données primitives de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(nombre, valeur booléenne ou chaîne\).  Si la valeur est un objet, l'objet est retourné sans modification.  Si la *valeur* est `null`, **non définie** ou non spécifiée, un objet sans contenu est créé.  
  
## Notes  
 L'objet `Object` est contenu dans tous les autres objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ; toutes ses méthodes et propriétés sont disponibles dans tous les autres objets.  Les méthodes peuvent être redéfinies dans les objets définis par l'utilisateur et sont appelées par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] au moment opportun.  La méthode **toString** est un exemple de méthode de l'objet `Object` fréquemment redéfinie.  
  
 Dans cette référence du langage, la description de chaque méthode `Object` fournit des informations à la fois sur des implémentations par défaut et des implémentations spécifiques aux objets pour les objets intrinsèques à [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Configuration requise  
 L'objet `Object Object` était une nouveauté d'[!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)].  Certains membres des listes suivantes ont été introduits dans les versions ultérieures.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Object Object`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété \_\_proto\_\_](../../javascript/reference/proto-property-object-javascript.md)|Spécifie le prototype pour un objet.|  
|[Propriété constructor](../../javascript/reference/constructor-property-object-javascript.md)|Spécifie la fonction qui crée un objet.|  
|[Propriété prototype](../../javascript/reference/prototype-property-object-javascript.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## Fonctions  
 Le tableau suivant répertorie les fonctions de l'`Object Object`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction Object.assign](../../javascript/reference/object-assign-function-object-javascript.md)|Copie les valeurs d'un ou de plusieurs objets sources dans un objet cible.|  
|[Fonction Object.create](../../javascript/reference/object-create-function-javascript.md)|Crée un objet qui a un prototype spécifié et qui contient éventuellement les propriétés spécifiées.|  
|[Fonction Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|Ajoute une ou plusieurs propriétés à un objet et\/ou modifie les attributs des propriétés existantes.|  
|[Fonction Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|Ajoute une propriété à un objet ou modifie les attributs d'une propriété existante.|  
|[Fonction Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Empêche la modification des attributs et valeurs de propriété existants, et empêche l'ajout de nouvelles propriétés.|  
|[Fonction Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Retourne la définition d'une propriété de données ou d'une propriété d'accesseur.|  
|[Fonction Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Retourne les noms des propriétés et méthodes d'un objet.|  
|[Object.getOwnPropertySymbols, fonction](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Retourne les symboles de propriété d'un objet.|  
|[Fonction Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|Retourne le prototype d'un objet.|  
|[Object.is, fonction](../../javascript/reference/object-is-function-javascript.md)|Retourne une valeur qui indique si deux valeurs sont identiques.|  
|[Fonction Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Retourne une valeur qui indique si de nouvelles propriétés peuvent être ajoutées à un objet.|  
|[Fonction Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Retourne la valeur `true` si les attributs et valeurs de propriété existants ne peuvent pas être modifiés dans un objet et que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.|  
|[Fonction Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Retourne la valeur `true` si les attributs de propriété existants ne peuvent pas être modifiés dans un objet et que de nouvelles propriétés ne peuvent pas être ajoutées à l'objet.|  
|[Fonction Object.keys](../../javascript/reference/object-keys-function-javascript.md)|Retourne les noms des propriétés et méthodes énumérables d'un objet.|  
|[Fonction Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Empêche l'ajout de nouvelles propriétés à un objet.|  
|[Fonction Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Empêche la modification des attributs des propriétés existantes et empêche l'ajout de nouvelles propriétés.|  
|[Object.setPrototypeOf, fonction](../../javascript/reference/object-setprototypeof-function-javascript.md)|Définit le prototype d'un objet.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'`Object Object`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la hiérarchie prototype d'un autre objet.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne qui indique si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retourne un objet converti en chaîne en fonction des paramètres régionaux actuels.|  
|[Méthode toString](../../javascript/reference/tostring-method-object-javascript.md)|Retourne la représentation d'un objet sous forme de chaîne.|  
|[Méthode valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Voir aussi  
 [JavaScript, objets](../../javascript/reference/javascript-objects.md)