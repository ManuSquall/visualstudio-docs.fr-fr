---
title: "JsNumberToInt (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsNumberToInt (fonction)
Récupère la valeur `int` d'une valeur numérique.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### Paramètres  
 `value`  
 Valeur numérique à convertir en valeur `int`.  
  
 `intValue`  
 Valeur de l'objet `int`.  
  
## Valeur de retour  
  
## Notes  
 Cette fonction récupère la valeur d'une valeur numérique et la convertit en valeur `int`.  Elle échoue avec `JsErrorInvalidArgument` si le type de la valeur n'est pas numérique.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)