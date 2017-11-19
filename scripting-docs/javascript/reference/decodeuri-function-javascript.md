---
title: decodeURI, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>decodeURI, fonction (JavaScript)
Obtient la version non encodée d’un encodé ressource identificateur URI (Uniform).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `URIstring` argument est une valeur qui représente un URI codé.  
  
 Utilisez le `decodeURI` fonction au lieu de déconseillées `unescape` (fonction).  
  
 Le `decodeURI` fonction retourne une valeur de chaîne.  
  
 Si le `URIString` n’est pas valide, une erreur URIError se produit.  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Exemple  
 Le code suivant, tout d’abord encode un composant d’URI, puis les décode.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Objet Global](../../javascript/reference/global-object-javascript.md)