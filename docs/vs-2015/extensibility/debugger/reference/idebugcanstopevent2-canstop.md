---
title: 'IDebugCanStopEvent2 :: CanStop | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191193"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indique au moteur de débogage s’il faut ou non arrêter à l’emplacement de code actuel ou simplement continuer l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fCanStop`  
 dans Différent de zéro ( `TRUE` ) si le de doit s’arrêter à l’emplacement de code actuel ; sinon, zéro ( `FALSE` ).  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le récepteur de cet événement appelle généralement la méthode [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) pour déterminer la raison pour laquelle le de souhaite s’arrêter, puis appelle la `IDebugCanStopEvent2::CanStop` méthode avec la réponse appropriée.  
  
 Si le DE s’arrête, il envoie un événement qui décrit la raison de l’arrêt. Il y a généralement deux événements qui sont envoyés, un saut d’utilisateur ou de signal représenté par l’interface [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) et un événement de point d’arrêt représenté par l’interface [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
