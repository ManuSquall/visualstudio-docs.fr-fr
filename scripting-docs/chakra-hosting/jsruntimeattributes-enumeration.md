---
title: "JsRuntimeAttributes, énumération | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimeattributes-enumeration"></a>JsRuntimeAttributes, énumération
Attributs d'un runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Le runtime doit prendre en charge l'interruption de script fiable. Cela augmente le nombre d'emplacements dans lesquels le runtime recherche une demande d'interruption de script en contrepartie d'une faible quantité des performances du runtime.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Le runtime n'effectue aucune tâche (par ex., une opération de garbage collection) sur les threads d'arrière-plan.|  
|`JsRuntimeAttributeDisableEval`|L'utilisation d'un constructeur `eval` ou `function` lève une exception.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Le runtime ne génère pas de code natif.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Le runtime autorise toutes les fonctionnalités expérimentales.|  
|`JsRuntimeAttributeEnableIdleProcessing`|L'hôte appelle `JsIdle`et active ainsi le traitement des temps d'inactivité. Sinon, le runtime gère la mémoire légèrement plus efficacement.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|L’appel de `JsSetException` distribue également l’exception au débogueur de script (le cas échéant), lui offrant la possibilité de s’arrêter sur l’exception.|  
|`JsRuntimeAttributeNone`|Aucun attribut spécial.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)