---
title: ATTACH_REASON | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2dc7736f9210ef15cec8cece45d7899cc116a334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Joindre](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)