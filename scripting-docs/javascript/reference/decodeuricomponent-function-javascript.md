---
title: "decodeURIComponent, fonction (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent (méthode)"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent, fonction (JavaScript)
Obtient la version non encodée d'un composant codé d'un identificateur URI.  
  
## Syntaxe  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## Notes  
 L'argument `encodedURIString` requis est une valeur qui représente un composant URI encodé.  
  
 Le composant URI fait partie intégrante d'un identificateur URI.  
  
 Si l'argument `encodedURIString` n'est pas valide, une erreur URIError se produit.  
  
## Exemple  
 Le code suivant encode, puis décode un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)