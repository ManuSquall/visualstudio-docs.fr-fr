---
title: "JsValueToVariant, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant (fonction)"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant, fonction
Initialise l'élément `VARIANT` transféré en tant que projection d'une valeur JavaScript.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### Paramètres  
 `object`  
 Valeur JavaScript à projeter en tant que `VARIANT`.  
  
 `variant`  
 Pointeur vers un struct `VARIANT` qui sera initialisé en tant que projection.  
  
## Valeur de retour  
  
## Notes  
 L'élément `VARIANT` de projection peut être utilisé par les clients COM Automation pour appeler l'objet JavaScript projeté.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)