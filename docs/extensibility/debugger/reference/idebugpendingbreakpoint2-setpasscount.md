---
title: IDebugPendingBreakpoint2::SetPassCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ab9a8ceec8c0f3a1b8d6c3c18fcf9c5c2a5b0b91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="remarks"></a>Notes  
 N’importe quel nombre de test qui a été précédemment associé avec le point d’arrêt en attente est perdue. Tous les points d’arrêt liés à partir de ce point d’arrêt dans l’attente sont appelées pour définir leur nombre passe la `bpPassCount` paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)