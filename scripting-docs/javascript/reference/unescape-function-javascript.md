---
title: "unescape, fonction (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape (méthode)"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape, fonction (JavaScript)
Décode les objets `String` encodés au moyen de la fonction `escape`.  Déconseillé.  
  
## Syntaxe  
  
```  
unescape(charString)   
```  
  
## Notes  
 L'argument `charString` requis est un objet `String` ou un littéral à décoder.  
  
 La fonction `unescape` retourne une valeur de chaîne reprenant le contenu de `charstring`.  Tous les caractères encodés sous la forme hexadécimale %*xx* sont remplacés par leur équivalent dans le jeu de caractères ASCII.  
  
 Les caractères encodés au format **%u** *xxxx* \(caractères Unicode\) sont remplacés par les caractères Unicode avec encodage hexadécimal *xxxx*.  
  
> [!NOTE]
>  N'utilisez pas la fonction `unescape` pour décoder des URI \(Uniform Resource Identifiers\).  Utilisez les fonctions `decodeURI` et `decodeURIComponent` à la place.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Fonction escape](../../javascript/reference/escape-function-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)