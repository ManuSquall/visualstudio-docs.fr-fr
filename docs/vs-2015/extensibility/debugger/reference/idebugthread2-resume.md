---
title: 'IDebugThread2 :: Resume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152993"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprend l’exécution d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 à Retourne le nombre de suspensions après l’opération de reprise.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque appel à cette méthode décrémente le nombre de suspension jusqu’à ce qu’il atteigne la valeur 0, à laquelle l’exécution reprend en fait. Ce nombre de suspensions s’affiche dans la fenêtre de débogage des **Threads** .  
  
 Pour chaque appel à cette méthode, il doit y avoir un appel antérieur à la méthode [suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Le nombre de suspensions détermine le nombre de fois `IDebugThread2::Suspend` que la méthode a été appelée jusqu’à présent.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
