---
title: IDebugThread2::Resume | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86402ceed6050b95e27df059d662e377c007aa67
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863345"
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
 [out] Retourne le nombre de suspend après l’opération de reprise.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque appel à cette méthode décrémente le compteur de suspension jusqu'à ce qu’il atteigne 0 à ce moment-là, l’exécution est reprise réellement. Ce compteur de suspension s’affiche dans le **Threads** fenêtre de débogage.  
  
 Pour chaque appel à cette méthode, il doit y avoir un appel précédent à la [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) (méthode). Le compteur de suspension détermine combien de fois le `IDebugThread2::Suspend` méthode a été appelée jusqu'à présent.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

