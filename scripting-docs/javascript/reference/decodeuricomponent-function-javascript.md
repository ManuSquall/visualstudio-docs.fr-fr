---
title: decodeURIComponent, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent, fonction (JavaScript)
Obtient la version non encodée d’un composant codé d’un identificateur de ressource uniforme (URI).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `encodedURIString` argument est une valeur représentant un composant d’URI encodé.  
  
 Un intégrante fait partie d’un URI complet.  
  
 Si le `encodedURIString` n’est pas valide, une erreur URIError se produit.  
  
## <a name="example"></a>Exemple  
 Le code suivant encode tout d’abord, puis les décode un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURI, fonction](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)