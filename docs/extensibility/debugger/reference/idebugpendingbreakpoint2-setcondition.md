---
title: IDebugPendingBreakpoint2::SetCondition | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bc50ad1d763f196944e6246f891c5b4ed3893da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115666"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Définit ou modifie la condition associée au point d’arrêt en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bpCondition`  
 [in] A [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) structure qui spécifie la condition à définir.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Toute condition qui a été précédemment associée avec le point d’arrêt en attente est perdue. Tous les points d’arrêt liés à partir de ce point d’arrêt dans l’attente sont appelées pour définir leur état à la valeur spécifiée dans le `bpCondition` paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)