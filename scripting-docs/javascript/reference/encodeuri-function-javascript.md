---
title: "encodeURI, fonction (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI (méthode)"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI, fonction (JavaScript)
Encode une chaîne de texte de façon à obtenir un identificateur URI \(Uniform Resource Identifier\) valide.  
  
## Syntaxe  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## Notes  
 L'argument `URIString` requis est une valeur qui représente un URI encodé.  
  
 La fonction `encodeURI` retourne un URI encodé.  Si vous passez le résultat à la méthode `decodeURI`, la chaîne d'origine est retournée.  La fonction `encodeURI` n'encode pas les caractères suivants : « : », « \/ », « ; » et « ? ».  Utilisez la méthode `encodeURIComponent` pour encoder ces caractères.  
  
## Exemple  
 Le code suivant encode, puis décode un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)