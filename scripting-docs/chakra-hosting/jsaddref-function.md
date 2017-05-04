---
title: "JsAddRef, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef (fonction)"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsAddRef, fonction
Ajoute une référence à un objet récupéré par le garbage collector.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### Paramètres  
 `ref`  
 Objet auquel ajouter une référence.  
  
 `count`  
 Nouveau nombre de références de l'objet \(peut avoir la valeur null\).  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Doit être appelé sur les handles `JsRef` qui ne vont pas être stockés dans la pile.  L'appel de `JsAddRef` garantit que l'objet auquel fait référence `JsRef` ne sera pas libéré tant que `JsRelease` n'est pas appelé.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)