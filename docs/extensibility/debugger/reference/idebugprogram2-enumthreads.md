---
title: IDebugProgram2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumThreads
helpviewer_keywords:
- IDebugProgram2::EnumThreads
ms.assetid: 0f2a8c51-1315-4c96-8aa1-6a937dc2a769
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de5beb17fd0ffd3ca6f21c40ebdde85cc74225f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915411"
---
# <a name="idebugprogram2enumthreads"></a>IDebugProgram2::EnumThreads
Récupère une liste des threads qui s’exécutent dans le programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumThreads(   
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(   
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) objet qui contient une liste des threads.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)