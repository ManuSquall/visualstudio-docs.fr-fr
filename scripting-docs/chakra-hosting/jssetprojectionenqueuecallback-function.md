---
title: JsSetProjectionEnqueueCallback, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568979"
---
# <a name="jssetprojectionenqueuecallback-function"></a>JsSetProjectionEnqueueCallback (fonction)
Définit le rappel à utiliser pour appeler la fin d'une projection vers le thread requis par les appelants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `projectionEnqueueContext`  
 Rappel à appeler à chaque fin de projection sur un thread d'arrière-plan.  
  
 `callbackState`  
 Contexte d'application fourni à `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 L'appel doit provenir d'un cloisonnement COM différent ou d'un thread différent dans le même MTA.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
> [!CAUTION]
>  PInvoke n'est pas pris en charge actuellement pour cette API.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)