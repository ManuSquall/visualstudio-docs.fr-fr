---
title: "JsSetRuntimeMemoryAllocationCallback, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryAllocationCallback"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryAllocationCallback (fonction)"
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryAllocationCallback, fonction
Définit un rappel d'allocation de mémoire pour un runtime spécifié  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### Paramètres  
 `runtime`  
 Runtime pour lequel enregistrer le rappel d'allocation.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
 `allocationCallback`  
 Rappel d'allocation de mémoire à appeler pour les événements d'allocation de mémoire.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 L'enregistrement d'un rappel d'allocation de mémoire entraîne le rappel de l'hôte par le runtime chaque fois qu'il obtient de la mémoire du système d'exploitation ou lui en donne.  La routine de rappel est appelée avant que le gestionnaire de mémoire du runtime alloue un bloc de mémoire.  L'allocation est rejetée si le rappel retourne la valeur false.  Le gestionnaire de mémoire du runtime appelle également la routine de rappel après la libération d'un bloc de mémoire, ainsi qu'après les échecs d'allocation.  
  
 Le rappel est appelé sur le thread d'exécution du runtime actuel, par conséquent, l'exécution est bloquée jusqu'à ce que le rappel soit terminé.  
  
 La valeur de retour du rappel n'est pas stockée. Les allocations précédemment rejetées n'empêchent pas le runtime d'appeler le rappel plus tard pour les nouvelles allocations de mémoire.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)