---
title: DES ÉTATS DU THREAD | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b62e8770449fc71a47d325d933b54b2090f59e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503951"
---
# <a name="threadstate"></a>THREADSTATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [des États du thread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/threadstate).  
  
Spécifie l’état du thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Indique que le thread a été créé, mais n’exécute pas encore de code.  
  
 THREADSTATE_DEAD  
 Indique que le thread est inactif.  
  
 THREADSTATE_FROZEN  
 Indique que le thread est figé (aucune exécution ne peut être effectuée).  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `dwThreadState` champ la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)

