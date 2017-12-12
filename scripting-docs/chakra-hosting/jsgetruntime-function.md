---
title: JsGetRuntime, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetRuntime
helpviewer_keywords: JsGetRuntime function
ms.assetid: 5b62e940-a885-405a-9fdd-0495fb391b95
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c313c70dfb0c792730d1f8001fb03dd7428294ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntime-function"></a>JsGetRuntime, fonction
Obtient le runtime auquel appartient le contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetRuntime(  
   _In_ JsContextRef context,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `context`  
 Contexte à partir duquel obtenir le runtime.  
  
 `runtime`  
 Runtime auquel appartient le contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)