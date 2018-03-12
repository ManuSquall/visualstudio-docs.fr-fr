---
title: ATTACH_REASON | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Spécifie la raison pour le moteur de débogage (DE) à attacher à un nœud du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 ATTACH_REASON_AUTO  
 Attacher, car le processus est actuellement en mode débogage.  
  
 ATTACH_REASON_LAUNCH  
 Attacher, car le processus a été lancé.  
  
 ATTACH_REASON_USER  
 Attacher en raison d’une demande de l’utilisateur.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont utilisées en tant que paramètre à la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) et [attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) méthodes.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Joindre](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)