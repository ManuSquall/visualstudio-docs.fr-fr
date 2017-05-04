---
title: "JsRuntimeAttributes, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes (énumération)"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# JsRuntimeAttributes, &#233;num&#233;ration
Attributs d'un runtime.  
  
## Syntaxe  
  
```  
enum JsRuntimeAttributes;  
```  
  
## Membres  
  
### Valeurs  
  
|Nom|Description|  
|---------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Le runtime doit prendre en charge l'interruption de script fiable. Cela augmente le nombre d'emplacements dans lesquels le runtime recherche une demande d'interruption de script en contrepartie d'une faible quantité des performances du runtime.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Le runtime n'effectue aucune tâche \(par ex., une opération de garbage collection\) sur les threads d'arrière\-plan.|  
|`JsRuntimeAttributeDisableEval`|L'utilisation d'un constructeur `eval` ou `function` lève une exception.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Le runtime ne génère pas de code natif.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Le runtime autorise toutes les fonctionnalités expérimentales.|  
|`JsRuntimeAttributeEnableIdleProcessing`|L'hôte appelle `JsIdle` et active ainsi le traitement des temps d'inactivité. Sinon, le runtime gère la mémoire légèrement plus efficacement.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|L’appel de `JsSetException` distribue également l’exception au débogueur de script \(le cas échéant\), lui offrant la possibilité de s’arrêter sur l’exception.|  
|`JsRuntimeAttributeNone`|Aucun attribut spécial.|  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)