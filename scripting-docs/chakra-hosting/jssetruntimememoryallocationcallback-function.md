---
title: JsSetRuntimeMemoryAllocationCallback, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords: JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback, fonction
Définit un rappel d'allocation de mémoire pour un runtime spécifié  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Runtime pour lequel enregistrer le rappel d'allocation.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
 `allocationCallback`  
 Rappel d'allocation de mémoire à appeler pour les événements d'allocation de mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 L’enregistrement d’un rappel d’allocation de mémoire entraîne le rappel de l’hôte par le runtime chaque fois qu’il obtient de la mémoire du système d’exploitation ou lui en donne. La routine de rappel est appelée avant que le gestionnaire de mémoire du runtime alloue un bloc de mémoire. L'allocation est rejetée si le rappel retourne la valeur false. Le gestionnaire de mémoire du runtime appelle également la routine de rappel après la libération d'un bloc de mémoire, ainsi qu'après les échecs d'allocation.  
  
 Le rappel est appelé sur le thread d'exécution du runtime actuel, par conséquent, l'exécution est bloquée jusqu'à ce que le rappel soit terminé.  
  
 La valeur de retour du rappel n'est pas stockée. Les allocations précédemment rejetées n'empêchent pas le runtime d'appeler le rappel plus tard pour les nouvelles allocations de mémoire.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)