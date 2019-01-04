---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8f088c9c1b56050ca59d2fb6e7a85eb8146077b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900133"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Définit le nombre d’accès pour le point d’arrêt lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```csharp  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwHitCount`  
 [in] Le nombre d’accès à définir.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_BP_DELETED` si l’état de l’objet de point d’arrêt lié est défini sur `BPS_DELETED` (dans le cadre de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) énumération).  
  
## <a name="remarks"></a>Notes  
 Le nombre d’accès est le nombre de fois où que ce point d’arrêt a été déclenchée pendant l’exécution de la session actuelle.  
  
 Cette méthode est généralement appelée par le moteur de débogage pour mettre à jour le nombre d’accès actuel sur ce point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)