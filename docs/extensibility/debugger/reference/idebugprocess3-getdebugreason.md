---
title: IDebugProcess3::GetDebugReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 733818736c6a6eaf8428a50aa9a1cf153d578a2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914064"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Cette méthode retourne la raison que le processus a été lancé pour le débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDebugReason(  
   DEBUG_REASON* pReason  
);  
```  
  
```csharp  
int GetDebugReason(  
   out enum_DEBUG_REASON pReason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pReason`  
 [out] Retourne une valeur de la [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)