---
title: DEBUG_REASON | Microsoft Docs
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
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 883630e7c9e00a58eac143a6cde7ee40109bb4e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516740"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DEBUG_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reason).  
  
Spécifie la raison pour laquelle le processus a été lancé pour le débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 DEBUG_REASON_ERROR  
 Une erreur non spécifique s’est produite (utilisé en tant qu’une condition par défaut lorsque aucune des autres raisons ajuster).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Le processus a été lancé à la demande de l’utilisateur.  
  
 DEBUG_REASON_USER_ATTACHED  
 Le processus en cours d’exécution a été attaché à par l’utilisateur.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Le processus a été automatiquement attaché à lorsqu’elle a été lancée.  
  
 DEBUG_REASON_CAUSALITY  
 Le processus a été lancé en raison un *juste-à-temps* événement de débogage (JIT).  
  
## <a name="remarks"></a>Notes  
 Retourné par la [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

