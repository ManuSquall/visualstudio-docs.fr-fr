---
title: encodeURI, fonction (JavaScript) | Documents Microsoft
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
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>encodeURI, fonction (JavaScript)
Encode une chaîne de texte comme une valide ressource identificateur URI (Uniform)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `URIString` argument est une valeur qui représente un URI codé.  
  
 Le `encodeURI` fonction retourne un URI codé. Si vous passez le résultat à `decodeURI`, la chaîne d’origine est retournée. Le `encodeURI` fonction n’encode pas les caractères suivants : « : », « / », « ; » et « ? ». Utilisez `encodeURIComponent` à la place.  
  
## <a name="example"></a>Exemple  
 Le code suivant encode tout d’abord, puis les décode un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURI, fonction](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)