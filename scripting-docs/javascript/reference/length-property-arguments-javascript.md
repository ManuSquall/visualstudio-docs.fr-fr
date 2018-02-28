---
title: "Length, propriété (arguments) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>length, propriété (arguments) (JavaScript)
Retourne le nombre réel d’arguments passés à une fonction par l’appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif *fonction* argument est le nom d’en cours d’exécution `Function` objet.  
  
 Le **longueur** propriété de la **arguments** objet est initialisé par le moteur de script au nombre réel d’arguments passés à un `Function` de l’objet au début de l’exécution de cette fonction.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **longueur** propriété de la **arguments** objet. Pour bien comprendre l’exemple, passer plusieurs arguments à la fonction que les 2 arguments attendu :  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique à**: [objet arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de fonction](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [arguments, propriété (fonction)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length, propriété (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriété length (Chaîne)](../../javascript/reference/length-property-string-javascript.md)