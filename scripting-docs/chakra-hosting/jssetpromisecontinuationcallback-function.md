---
title: JsSetPromiseContinuationCallback, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6ef0faf4-1500-4bd9-aeca-c208492af8ea
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c20b5c81bd34a44158a975f0c1aed88614e01022
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568649"
---
# <a name="jssetpromisecontinuationcallback-function"></a>JsSetPromiseContinuationCallback (fonction)
Définit une fonction de rappel de continuation de promesse qui est appelée par le contexte quand une tâche doit être mise en attente pour une exécution ultérieure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetPromiseContinuationCallback(  
   _In_ JsPromiseContinuationCallback promiseContinuationCallback,  
   _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `promiseContinuationCallback`  
 Fonction de rappel définie.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)