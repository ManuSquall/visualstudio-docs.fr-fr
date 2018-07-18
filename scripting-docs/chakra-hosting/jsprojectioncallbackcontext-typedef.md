---
title: JsProjectionCallbackContext, typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568419"
---
# <a name="jsprojectioncallbackcontext-typedef"></a>JsProjectionCallbackContext (typedef)
Contexte passé dans le rappel de l'application, JsProjectionEnqueueCallback, de JsRT et ensuite repassé à JsRT dans le rappel fourni, `JsProjectionCallback`, par l'application sur le thread approprié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Remarques  
 Nécessite l'appel de `JsSetProjectionEnqueueCallback` pour recevoir des rappels.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)