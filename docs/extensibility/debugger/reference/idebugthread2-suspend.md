---
title: IDebugThread2::Suspend | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: aa00d0029120abad26a7f4fdcd15f828a0284f2f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Interrompt un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwSuspendCount`  
 [out] Retourne le compteur de suspension après l’opération de suspension.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque appel à cette méthode incrémente le compteur de suspension supérieure à 0. Ce compteur de suspension est affiché dans le **Threads** fenêtre de débogage.  
  
 Pour chaque appel à cette méthode, il doit y avoir un appel ultérieur à la [reprise](../../../extensibility/debugger/reference/idebugthread2-resume.md) méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Reprise](../../../extensibility/debugger/reference/idebugthread2-resume.md)
