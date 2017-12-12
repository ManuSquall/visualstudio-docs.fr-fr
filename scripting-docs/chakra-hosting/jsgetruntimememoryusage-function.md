---
title: JsGetRuntimeMemoryUsage, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetRuntimeMemoryUsage
helpviewer_keywords: JsGetRuntimeMemoryUsage function
ms.assetid: b9bd4146-bfbc-4cb1-a0e9-a0ded7fb09bd
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3519e4395ab5b3b7bbc5186c56775bdef9b12ecf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntimememoryusage-function"></a>JsGetRuntimeMemoryUsage, fonction
Obtient l'utilisation de mémoire actuelle pour un runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryUsage(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryUsage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Runtime dont l'utilisation de mémoire doit être récupérée.  
  
 `memoryUsage`  
 Utilisation mémoire actuelle du runtime, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 L'utilisation de mémoire peut toujours être récupérée, que le runtime soit actif ou non sur un autre thread.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)