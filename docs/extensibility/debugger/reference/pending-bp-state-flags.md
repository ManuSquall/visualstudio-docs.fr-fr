---
title: PENDING_BP_STATE_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE_FLAGS
helpviewer_keywords: PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c312123b9782b892f6ce99d7e7684b1622e75381
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
Spécifie les indicateurs d’état de point d’arrêt en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>Membres  
 PBPSF_NONE  
 Espace réservé.  
  
 PBPSF_VIRTUALIZED  
 Spécifie un virtualisé en attente de point d’arrêt, qui doit être liée à chaque chargement de nouveau code.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `flags` membre de la [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) structure.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)