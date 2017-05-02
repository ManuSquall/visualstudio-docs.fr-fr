---
title: "JsHasException, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException (fonction)"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException, fonction
Détermine si le runtime du contexte actuel est dans un état d'exception.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### Paramètres  
 `hasException`  
 Indique si le runtime du contexte actuel est dans l'état d'exception.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Si un appel dans les résultats du runtime d'une exception \(comme le résultat de l'exécution d'un script ou en raison d'un événement tel qu'un échec de conversion\), le runtime est placé dans un « état d'exception ». Tous les appels dans n'importe quel contexte créé par le runtime \(à l'exception des API d'exception\) échouent avec `JsErrorInExceptionState` tant que l'exception n'est pas désactivée.  
  
 Si le runtime du contexte actuel est dans l'état d'exception quand un rappel retourne dans le moteur, ce dernier relève automatiquement l'exception.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)