---
title: IDebugThread2::Resume | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::Resume
helpviewer_keywords: IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25b0f663b6f512cbe8ea6eaafa2167a6828280c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Reprend l’exécution d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwSuspendCount`  
 [out] Retourne le compteur de suspension après l’opération de reprise.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Chaque appel à cette méthode décrémente le compteur de suspension jusqu'à ce qu’il atteigne 0 à ce moment-là, l’exécution est réellement reprise. Ce compteur de suspension s’affiche dans le **Threads** fenêtre de débogage.  
  
 Pour chaque appel à cette méthode, il doit y avoir un appel précédent à la [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) (méthode). Le compteur de suspension détermine combien de fois le `IDebugThread2::Suspend` méthode a été appelée jusqu'à présent.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)