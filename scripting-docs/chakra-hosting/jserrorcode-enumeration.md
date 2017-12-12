---
title: "JsErrorCode, énumération | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsErrorCode
helpviewer_keywords: JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jserrorcode-enumeration"></a>JsErrorCode, énumération
Code d'erreur retourné par une API d'hébergement Chakra.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|Le contexte ne peut pas être placé en état de débogage, car il se trouve déjà dans cet état.|  
|`JsErrorAlreadyProfilingContext`|Le contexte ne peut pas démarrer le profilage, car ce dernier est déjà démarré.|  
|`JsErrorArgumentNotObject`|Une API d'hébergement qui fonctionne sur des valeurs d'objet a été appelée avec une valeur non-objet.|  
|`JsErrorBadSerializedScript`|Un script sérialisé incorrect a été utilisé, ou le script sérialisé a été sérialisé par une autre version du moteur Chakra.|  
|`JsErrorCannotDisableExecution`|Le runtime ne prend pas en charge l'interruption de script fiable.|  
|`JsErrorCannotSerializeDebugScript`|Les scripts ne peuvent pas être sérialisés dans des contextes de débogage.|  
|`JsErrorCategoryEngine`|Catégorie d'erreurs relative aux erreurs qui se produisent au sein du moteur.|  
|`JsErrorCategoryFatal`|Catégorie d'erreurs irrécupérables qui indiquent l'échec du moteur.|  
|`JsErrorCategoryScript`|Catégorie d'erreurs relative aux erreurs dans un script.|  
|`JsErrorCategoryUsage`|Catégorie d'erreurs relative à une utilisation incorrecte de l'API.|  
|`JsErrorFatal`|Une erreur irrécupérable s'est produite dans le moteur.|  
|`JsErrorHeapEnumInProgress`|Une énumération de tas est actuellement en cours d'exécution dans le contexte de script.|  
|`JsErrorIdleNotEnabled`|Notification d'inactivité envoyée quand l'hôte n'a pas activé le traitement des temps d'inactivité.|  
|`JsErrorInDisabledState`|Le runtime est dans un état désactivé.|  
|`JsErrorInExceptionState`|Le moteur est dans un état d'exception et aucune API ne peut être appelée avant la désactivation de l'exception.|  
|`JsErrorInObjectBeforeCollectCallback`|L'opération n'est pas prise en charge dans un objet avant le rappel de collecte.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsErrorInProfileCallback`|Un contexte de script est en train de rappeler un profil.|  
|`JsErrorInThreadServiceCallback`|Un rappel de service de thread est en cours d'exécution.|  
|`JsErrorInvalidArgument`|Un argument pour une API d'hébergement n'était pas valide.|  
|`JsErrorNoCurrentContext`|L'API d'hébergement requiert qu'un contexte soit actif, mais aucun contexte n'est actif.|  
|`JsErrorNotImplemented`|Une API d'hébergement n'est pas encore implémentée.|  
|`JsErrorNullArgument`|Un argument pour une API d'hébergement avait la valeur null dans un contexte où cette valeur n'est pas autorisée.|  
|`JsErrorObjectNotInspectable`|L'objet ne peut pas être désencapsulé dans un pointeur `IInspectable` .<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsErrorOutOfMemory`|Mémoire insuffisante pour exécuter le moteur Chakra.|  
|`JsErrorPropertyNotSymbol`|Une API d'hébergement qui fonctionne sur des ID de propriété sous forme de symboles a été appelée avec un ID de propriété qui n'est pas un symbole. Le code d'erreur est retourné par `JsGetSymbolFromPropertyId` si la fonction est appelée avec un ID de propriété qui n'est pas un symbole.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsErrorPropertyNotString`|Une API d'hébergement qui fonctionne sur des ID de propriété sous forme de chaînes a été appelée avec un ID de propriété qui n'est pas une chaîne. Le code d'erreur est retourné par `JsGetPropertyNamefromId` si la fonction est appelée avec un ID de propriété qui n'est pas une chaîne.<br /><br /> Cette valeur d'énumération est prise en charge uniquement dans le mode Edge.|  
|`JsErrorRuntimeInUse`|Un runtime en cours d'utilisation ne peut pas être supprimé.|  
|`JsErrorScriptCompile`|La compilation JavaScript a échoué.|  
|`JsErrorScriptEvalDisabled`|Un script a été arrêté, car il a tenté d'utiliser `eval` ou `function` et eval était désactivé.|  
|`JsErrorScriptException`|Une exception JavaScript s'est produite pendant l'exécution d'un script.|  
|`JsErrorScriptTerminated`|Un script a été arrêté en raison d'une demande de suspension de runtime.|  
|`JsErrorWrongRuntime`|Une API d’hébergement a été appelée avec un objet créé sur un autre runtime JavaScript.|  
|`JsErrorWrongThread`|Une API d'hébergement a été appelée sur le thread incorrect.|  
|`JsNoError`|Code d'erreur de réussite.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)