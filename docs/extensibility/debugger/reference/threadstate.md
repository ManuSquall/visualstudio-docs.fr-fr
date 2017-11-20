---
title: THREADSTATE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADSTATE
helpviewer_keywords: THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 495425e8a91d42d1da4c3a36f7e3be1e02031329
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="threadstate"></a>THREADSTATE
Spécifie l’état du thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Membres  
 THREADSTATE_RUNNING  
 Indique que le thread est en cours d’exécution.  
  
 THREADSTATE_STOPPED  
 Indique que le thread est arrêté en raison d’un point d’arrêt.  
  
 THREADSTATE_FRESH  
 Indique que le thread a été créé, mais n’est pas encore exécuté de code.  
  
 THREADSTATE_DEAD  
 Indique que le thread est inactif.  
  
 THREADSTATE_FROZEN  
 Indique que le thread est figé (aucune exécution ne peut être effectuée).  
  
## <a name="remarks"></a>Remarques  
 Utilisé pour le `dwThreadState` champ le [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)