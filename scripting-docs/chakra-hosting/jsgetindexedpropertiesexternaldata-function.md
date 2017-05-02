---
title: "JsGetIndexedPropertiesExternalData (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2c313163-3462-42fd-8dee-3dfb3ac7f43f
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetIndexedPropertiesExternalData (fonction)
Récupère les données externes des propriétés indexées d'un objet.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ void** data,  
   _Out_ JsTypedArrayType* arrayType,  
   _Out_ unsigned int* elementLength  
);  
```  
  
#### Paramètres  
 `object`  
 Objet.  
  
 `data`  
 Magasin de stockage des données externes pour les propriétés indexées de l'objet.  
  
 `arrayType`  
 Type d'élément de tableau dans les données externes.  
  
 `elementLength`  
 Nombre d'éléments de tableau dans les données externes.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)