---
title: "findIndex, méthode (Array) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="findindex-method-array-javascript"></a>findIndex, méthode (Array) (JavaScript)
Retourne une valeur d'index pour le premier élément du tableau qui répond aux critères de test spécifiés dans une fonction de rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet Array.  
  
 `callbackfn`  
 Obligatoire. Fonction de rappel pour tester chaque élément dans le tableau.  
  
 `thisArg`  
 Facultatif. Spécifie l'objet `this` dans la fonction de rappel. Si aucune valeur n'est spécifiée, l'objet `this` n'est pas défini.  
  
## <a name="remarks"></a>Remarques  
 La méthode `findIndex` appelle la fonction de rappel une fois pour chaque élément du tableau, dans l'ordre croissant, jusqu'à ce qu'un élément retourne `true`. Dès qu'un élément retourne true, `findIndex` retourne la valeur d'index de l'élément qui retourne la valeur true. Si aucun élément du tableau ne retourne true, `findIndex` retourne -1.  
  
 `findIndex` ne mute pas l'objet Array.  
  
## <a name="callback-function-syntax"></a>Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, index, thisArg)`  
  
 Vous pouvez déclarer la fonction de rappel avec trois paramètres maximum.  
  
 Les paramètres de la fonction de rappel sont les suivants :  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`arrayObj`|Objet Array à traverser.|  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, la fonction de rappel vérifie si chaque élément du tableau est égal à 2.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la syntaxe de fonction Arrow pour tester chaque élément. Dans cet exemple, aucun élément ne retourne `true`, et `findIndex` retourne -1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]