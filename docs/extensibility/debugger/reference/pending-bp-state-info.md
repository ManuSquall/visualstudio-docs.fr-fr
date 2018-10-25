---
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98c815c5f92930c3877e78ab27934b9abe199cef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947821"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Contient des informations sur l’état d’un point d’arrêt est prêt à lier à un emplacement de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Membres  
 état  
 Une valeur comprise entre le [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) énumération qui spécifie l’état de point d’arrêt en attente.  
  
 flags  
 Une combinaison d’indicateurs de la [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) énumération qui spécifie si le point d’arrêt est virtualisé.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) méthode où il est renseigné.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)