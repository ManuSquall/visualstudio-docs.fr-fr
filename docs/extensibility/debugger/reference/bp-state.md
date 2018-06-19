---
title: BP_STATE | Documents Microsoft
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
ms.openlocfilehash: a8908b61323c80891f93158046b9c7e821287d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110040"
---
# <a name="bpstate"></a>BP_STATE
Spécifie l’existence d’un point d’arrêt lié et spécifie également s’il est activé.  
  
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
 Spécifie qu’aucun point d’arrêt n’existe.  
  
 BPS_DELETED  
 Spécifie que le point d’arrêt a été supprimé.  
  
 BPS_DISABLED  
 Spécifie que le point d’arrêt est désactivé.  
  
 BPS_ENABLED  
 Spécifie que le point d’arrêt est activé.  
  
## <a name="remarks"></a>Notes  
 Retourné par la [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)