---
title: IDebugCanStopEvent2::CanStop | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::CanStop
helpviewer_keywords: IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9008410831d3c2c7b6e93d4f35a1d08914a5336
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifie le moteur de débogage (DE) ou non s’arrêter à l’emplacement du code en cours ou simplement de poursuivre l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] Non nul (`TRUE`) le DE doit s’arrêter à l’emplacement du code en cours ; sinon, zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le récepteur de cet événement appelle généralement la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) méthode pour déterminer la raison pour laquelle le DE souhaite arrêter, puis appelle la `IDebugCanStopEvent2::CanStop` méthode avec la réponse appropriée.  
  
 Si le DE s’arrête, il envoie un événement qui décrit la raison de l’arrêt. Il existe généralement deux événements sont envoyés, un saut de l’utilisateur ou de signal représenté par le [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interface et un événement de point d’arrêt représenté par le [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)