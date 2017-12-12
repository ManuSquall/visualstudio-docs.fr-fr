---
title: JsStopProfiling, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStopProfiling
helpviewer_keywords: JsStopProfiling function
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bed003e848a7ac34100a322275be04213da76e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsstopprofiling-function"></a>JsStopProfiling, fonction
Arrête le profilage dans le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `reason`  
 Raison pour laquelle le profilage cesse de transmettre au rappel de profileur.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Ne retourne pas d'erreur si le profilage n'a pas démarré.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge dans les applications de bureau, mais ne l'est pas dans les applications du Windows Store.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)