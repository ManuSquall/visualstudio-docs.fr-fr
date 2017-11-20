---
title: IDebugErrorBreakpoint2::GetPendingBreakpoint | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorBreakpoint2::GetPendingBreakpoint
helpviewer_keywords: IDebugErrorBreakpoint2::GetPendingBreakpoint
ms.assetid: 59d0defc-99fd-445c-bdac-8224d5dea3f9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c92a8463d0a92293dc448272a889524127d703e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorbreakpoint2getpendingbreakpoint"></a>IDebugErrorBreakpoint2::GetPendingBreakpoint
Obtient le point d’arrêt en attente qui a provoqué l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPendingBreakpoint (   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```csharp  
int GetPendingBreakpoint (   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppPendingBreakpoint`  
 [out] Retourne un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objet qui représente le point d’arrêt en attente qui n’a pas pu être lié.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)