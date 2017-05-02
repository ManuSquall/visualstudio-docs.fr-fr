---
title: "JsNativeFunction, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsNativeFunction, typedef
Un rappel de fonction.  
  
## Syntaxe  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### Paramètres  
 appelé  
 Un objet `Function` qui représente la fonction appelée.  
  
 isConstructCall  
 Indique s'il s'agit d'un appel régulier ou d'un « nouvel » appel.  
  
 arguments  
 Les arguments pour l'appel.  
  
 argumentCount  
 Le nombre d'arguments.  
  
## Valeur de propriété\/valeur de retour  
 Le résultat de l'appel, s'il y en a un.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)