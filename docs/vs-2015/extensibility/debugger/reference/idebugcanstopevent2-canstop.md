---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951996"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifie le moteur de débogage (dé) s’il faut arrêter à l’emplacement du code en cours ou simplement poursuivre l’exécution.  
  
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
