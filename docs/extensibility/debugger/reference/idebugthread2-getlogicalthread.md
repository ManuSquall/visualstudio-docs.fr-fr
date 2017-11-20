---
title: IDebugThread2::GetLogicalThread | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetLogicalThread
helpviewer_keywords: IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0f2eaba3176ed5d77a2857a4325a06b16417380
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Moteurs de débogage n’implémentent pas cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 [in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objet qui représente le frame de pile.  
  
 `ppLogicalThread`  
 [out] Retourne un `IDebugLogicalThread2` interface qui représente le thread logique associé. Une implémentation du moteur de débogage doit lui affecter une valeur null.  
  
## <a name="return-value"></a>Valeur de retour  
 Déboguer des implémentations de moteur retournent toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)