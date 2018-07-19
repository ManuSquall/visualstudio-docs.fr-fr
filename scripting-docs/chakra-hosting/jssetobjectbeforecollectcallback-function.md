---
title: JsSetObjectBeforeCollectCallback, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568919"
---
# <a name="jssetobjectbeforecollectcallback-function"></a>JsSetObjectBeforeCollectCallback (fonction)
Définit une fonction de rappel appelée par le runtime avant le garbage collection d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ref`  
 Objet pour lequel inscrire le rappel.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
 `objectBeforeCollectCallback`  
 Fonction de rappel définie. Utilisez null pour effacer le rappel précédemment inscrit.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Le rappel est appelé sur le thread d'exécution du runtime actuel, par conséquent, l'exécution est bloquée jusqu'à ce que le rappel soit terminé.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)