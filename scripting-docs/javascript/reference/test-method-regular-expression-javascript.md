---
title: test, méthode (Regular Expression) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640749"
---
# <a name="test-method-regular-expression-javascript"></a>test, méthode (Regular Expression) (JavaScript)
Retourne une valeur booléenne qui indique si un modèle existe dans une chaîne recherchée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Paramètres  
 `rgExp`  
 Obligatoire. Une instance d’un **Expression régulière** objet qui contient le modèle d’expression régulière et les indicateurs applicables.  
  
 `str`  
 Obligatoire. La chaîne sur laquelle effectuer la recherche.  
  
## <a name="remarks"></a>Remarques  
 Le **test** méthode vérifie si un modèle existe dans une chaîne et retourne **true** dans ce cas, et **false** dans le cas contraire.  
  
 Les propriétés de l’élément global `RegExp` objet ne sont pas modifiées par le **test** (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **test** (méthode). Pour utiliser cet exemple, passez à la fonction un modèle d’expression régulière et une chaîne. La fonction de test pour l’occurrence d’un modèle d’expression régulière dans la chaîne et retourne une chaîne indiquant les résultats de recherche :  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)