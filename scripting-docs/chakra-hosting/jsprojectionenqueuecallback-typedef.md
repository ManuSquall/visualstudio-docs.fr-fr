---
title: JsProjectionEnqueueCallback, typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectionenqueuecallback-typedef"></a>JsProjectionEnqueueCallback (typedef)
Rappel d'application effectué par JsRT quand une API de projection est exécutée sur un thread différent de celui d'origine.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `jsCallback`  
 Rappel à effectuer sur le thread d'origine.  
  
 `jsContext`  
 Contexte des applications.  
  
 `callbackState`  
 Contexte JsRT qui doit être passé dans `jsCallback`.  
  
## <a name="remarks"></a>Remarques  
 Nécessite l'appel de JsSetProjectionEnqueueCallback pour recevoir des rappels.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)