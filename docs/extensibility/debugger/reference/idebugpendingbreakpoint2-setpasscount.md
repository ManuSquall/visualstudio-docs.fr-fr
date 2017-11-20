---
title: IDebugPendingBreakpoint2::SetPassCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f56deacf0efe569890ed659ff5f59287483fb1a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Définit ou modifie le nombre de passe associé au point d’arrêt en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bpPassCount`  
 [in] A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) structure qui contient le nombre de test.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_BP_DELETED` si le point d’arrêt a été supprimé.  
  
## <a name="remarks"></a>Remarques  
 N’importe quel nombre de test qui a été précédemment associé avec le point d’arrêt en attente est perdue. Tous les points d’arrêt liés à partir de ce point d’arrêt dans l’attente sont appelées pour définir leur nombre passe la `bpPassCount` paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)