---
title: BP_STATE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0527cefeaed58e990d8474c25a522788e4dba6fa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924243"
---
# <a name="bpstate"></a>BP_STATE
Spécifie l’existence d’un point d’arrêt lié ainsi que si elle est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 BPS_NONE  
 Spécifie qu’il n’existe aucun point d’arrêt.  
  
 BPS_DELETED  
 Spécifie que le point d’arrêt a été supprimé.  
  
 BPS_DISABLED  
 Spécifie que le point d’arrêt est désactivé.  
  
 BPS_ENABLED  
 Spécifie que le point d’arrêt est activé.  
  
## <a name="remarks"></a>Notes  
 Retourné par la [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)