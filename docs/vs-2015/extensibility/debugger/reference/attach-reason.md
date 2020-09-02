---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c66894fe0515b28037bbb2a19715fa09cbf9fa62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153587"
---
# <a name="attach_reason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie la raison pour laquelle le moteur de débogage (DE) doit être attaché à un nœud de programme.  
  
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
 Attachement, car le processus est actuellement en mode débogage.  
  
 ATTACH_REASON_LAUNCH  
 Attachement, car le processus a été lancé.  
  
 ATTACH_REASON_USER  
 Attachement en raison d’une demande de l’utilisateur.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont utilisées comme paramètre pour les méthodes d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) et d' [attachement](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
