---
title: Boolean (objet) (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Boolean, objet (JavaScript)
Crée une valeur booléenne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Paramètres  
 `boolObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Boolean` est assigné.  
  
 `boolValue`  
 Facultatif. Valeur booléenne initiale du nouvel objet. Si `boolvalue` est omis ou a `false`, 0, `null`, `NaN`, ou une chaîne vide, la valeur initiale de l’objet Boolean est `false`. Sinon, la valeur initiale est `true`.  
  
## <a name="remarks"></a>Remarques  
 Le `Boolean` objet est un wrapper pour le type de données booléen. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]utilise implicitement la `Boolean` objet chaque fois qu’un type de données booléen est converti en un `Boolean` objet.  
  
 Il est rarement d’instancier le `Boolean` explicitement l’objet.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Boolean`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-boolean.md)|Spécifie la fonction qui crée une valeur booléenne.|  
|[prototype, propriété](../../javascript/reference/prototype-property-boolean.md)|Retourne une référence au prototype pour un booléen.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Boolean`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ToString, méthode](../../javascript/reference/tostring-method-boolean-1.md)|Retourne une représentation sous forme de chaîne d’une valeur booléenne.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-boolean.md)|Obtient une référence à la valeur booléenne.|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]