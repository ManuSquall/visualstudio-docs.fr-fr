---
title: "JsSetIndexedPropertiesToExternalData (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsSetIndexedPropertiesToExternalData (fonction)
Définit les propriétés indexées d'un objet dans des données externes.  Les données externes serviront de magasin de stockage des propriétés indexées de l'objet. Elles seront accessibles de la même manière qu'un tableau typé.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### Paramètres  
 `object`  
 Objet à utiliser.  
  
 `data`  
 Données externes à utiliser comme magasin de stockage des propriétés indexées de l'objet.  
  
 `arrayType`  
 Type d'élément de tableau dans les données externes.  
  
 `elementLength`  
 Nombre d'éléments de tableau dans les données externes.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)