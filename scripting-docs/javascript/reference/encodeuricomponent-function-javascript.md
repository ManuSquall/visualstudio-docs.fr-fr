---
title: encodeURIComponent, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent, fonction (JavaScript)
Encode une chaîne de texte comme un composant valide d’un identificateur de ressource uniforme (URI).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `encodedURIString` argument est une valeur représentant un composant d’URI encodé.  
  
 Le `encodeURIComponent` fonction retourne un URI codé. Si vous passez le résultat à `decodeURIComponent`, la chaîne d’origine est retournée. Étant donné que la `encodeURIComponent` fonction encode tous les caractères, soyez prudent si la chaîne représente un chemin d’accès tel que **/folder1/folder2/default.html**. Les caractères de barre oblique seront encodés et ne seront plus valides si envoyé en tant que demande à un serveur web. Utilisez le `encodeURI` fonctionne si la chaîne contient plusieurs composants URI unique.  
  
## <a name="example"></a>Exemple  
 Le code suivant, tout d’abord encode un composant d’URI, puis les décode.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURI, fonction](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)