---
title: "decodeURI, fonction (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI (méthode)"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI, fonction (JavaScript)
Obtient la version non encodée d'un URI \(Uniform Resource Identifier\) encodé.  
  
## Syntaxe  
  
```  
decodeURI(URIstring)  
```  
  
## Notes  
 L'argument `URIstring` requis est une valeur qui représente un URI encodé.  
  
 Préférez la fonction `decodeURI` à la fonction `unescape` qui est déconseillée.  
  
 La fonction `decodeURI` retourne une valeur de chaîne.  
  
 Si l'argument `URIString` n'est pas valide, une erreur URIError se produit.  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Exemple  
 Le code suivant encode, puis décode un composant URI.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Objet Global](../../javascript/reference/global-object-javascript.md)