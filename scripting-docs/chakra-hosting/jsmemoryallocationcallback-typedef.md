---
title: Jsmemoryallocationcallback, Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568729"
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback, typedef
Routine de rappel implémentée par l'utilisateur pour les événements d'allocation mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 callbackState  
 L'état passé à JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Le type d'événement d'allocation de type.  
  
 allocationSize  
 La taille de l'allocation.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Pour l'événement JsMemoryAllocate, le fait de retourner true autorise le runtime à continuer l'allocation. Si false est retourné, cela signifie que la demande d'allocation est rejetée. La valeur retournée est ignorée pour les autres événements d'allocation.  
  
## <a name="remarks"></a>Remarques  
 Utilisez JsSetRuntimeMemoryAllocationCallback pour inscrire ce rappel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)