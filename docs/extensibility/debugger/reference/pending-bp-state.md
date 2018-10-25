---
title: PENDING_BP_STATE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 30e70c956afc6aef5025d35425fbc2ee42605b90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921058"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Spécifie l’état d’un point d’arrêt en attente (un point d’arrêt qui n’a pas encore été lié).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 PBPS_NONE  
 Espace réservé pour un zéro. Cette valeur n’est jamais retournée.  
  
 PBPS_DELETED  
 Indique que le point d’arrêt en attente a été supprimé.  
  
 PBPS_DISABLED  
 Indique que le point d’arrêt en attente est désactivée.  
  
 PBPS_ENABLED  
 Indique que le point d’arrêt en attente est activée.  
  
## <a name="remarks"></a>Notes  
 Utiliser comme la `state` membre de la [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) structure.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)