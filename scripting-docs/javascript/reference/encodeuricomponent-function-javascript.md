---
title: "encodeURIComponent, fonction (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent (méthode)"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent, fonction (JavaScript)
Encode une chaîne de texte de façon à obtenir un composant valide d'un identificateur URI \(Uniform Resource Identifier\).  
  
## Syntaxe  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## Notes  
 L'argument `encodedURIString` requis est une valeur qui représente un composant URI encodé.  
  
 La fonction `encodeURIComponent` retourne un URI encodé.  Si vous passez le résultat à la méthode `decodeURIComponent`, la chaîne d'origine est retournée.  La fonction `encodeURIComponent` encodant tous les caractères, vous devez être prudent si la chaîne représente un chemin d'accès tel que \/dossier1\/dossier2\/default.html.  Les caractères de barre oblique seront encodés et ne seront pas valides s'ils sont envoyés sous forme de demande à un serveur Web.  Utilisez la fonction `encodeURI` si la chaîne contient plusieurs composants URI.  
  
## Exemple  
 Le code suivant encode, puis décode un composant URI.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)