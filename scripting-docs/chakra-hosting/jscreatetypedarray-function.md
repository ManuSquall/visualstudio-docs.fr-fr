---
title: "JsCreateTypedArray (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateTypedArray (fonction)
Crée un objet tableau typé JavaScript.  
  
## Syntaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Paramètres  
 `arrayType`  
 Type du tableau à créer.  
  
 `baseArray`  
 Tableau de base du nouveau tableau.  Utilisez `JS_INVALID_REFERENCE` s'il n'y a pas de tableau de base.  
  
 `byteOffset`  
 Décalage, en octets, à partir du début de `baseArray` \(`ArrayBuffer`\) pour le tableau typé résultant à référencer.  S'applique uniquement quand `baseArray` est un objet `ArrayBuffer`.  Sinon, doit avoir la valeur 0.  
  
 `elementLength`  
 Nombre d'éléments dans le tableau.  S'applique uniquement pour la création d'un tableau typé sans `baseArray` \(où `baseArray` est `JS_INVALID_REFERENCE`\) ou quand `baseArray` est un objet `ArrayBuffer`.  Sinon, doit avoir la valeur 0.  
  
 `result`  
 Nouvel objet tableau typé.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 `baseArray` peut être un objet `ArrayBuffer`, un autre tableau typé ou un objet `Array` JavaScript.  Le tableau typé retourné utilise `baseArray` s'il s'agit d'un objet `ArrayBuffer`. Sinon, une copie du tableau source sous\-jacent est créée et utilisée.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)