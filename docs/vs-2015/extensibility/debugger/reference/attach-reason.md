---
title: ATTACH_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff2c71418f3586c2915f1d4f4f4ff2fe37ed9bf4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873602"
---
# <a name="attachreason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie la raison pour le moteur de débogage (dé) à attacher à un nœud de programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

