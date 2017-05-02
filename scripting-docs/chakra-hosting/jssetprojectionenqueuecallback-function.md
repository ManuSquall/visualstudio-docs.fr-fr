---
title: "JsSetProjectionEnqueueCallback (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsSetProjectionEnqueueCallback (fonction)
Définit le rappel à utiliser pour appeler la fin d'une projection vers le thread requis par les appelants.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### Paramètres  
 `projectionEnqueueContext`  
 Rappel à appeler à chaque fin de projection sur un thread d'arrière\-plan.  
  
 `callbackState`  
 Contexte d'application fourni à `projectionEnqueueContext`.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Nécessite un contexte de script actif.  
  
 L'appel doit provenir d'un cloisonnement COM différent ou d'un thread différent dans le même MTA.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
> [!CAUTION]
>  PInvoke n'est pas pris en charge actuellement pour cette API.  
  
## Configuration requise  
 **En\-tête** : jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)