---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74c548df0aaffdca4dafc8851fa29e18c5ff4528
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954759"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifie le moteur de débogage (dé) s’il faut arrêter à l’emplacement du code en cours ou simplement poursuivre l’exécution.  
  
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
 [in] Valeur différente de zéro (`TRUE`) le DE doit s’arrêter à l’emplacement de code actuel ; sinon, zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le récepteur de cet événement appelle généralement la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) méthode pour déterminer la raison pour laquelle le DE veut arrêter, puis appelle la `IDebugCanStopEvent2::CanStop` méthode avec la réponse appropriée.  
  
 Si le dé s’arrête, il envoie un événement qui décrit la raison de l’arrêt. Il existe généralement deux événements sont envoyés, un saut de l’utilisateur ou de signal représenté par le [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interface et un événement de point d’arrêt représenté par le [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)