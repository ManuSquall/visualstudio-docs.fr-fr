---
title: IDebugThread2::GetName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetName
helpviewer_keywords: IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c608c01b788c88385814fced4fae99d267e96f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtient le nom d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 [out] Retourne le nom du thread.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le nom récupéré est toujours un nom qui peut être affiché et ce nom décrit le thread. Le nom de thread peut être dérivé d’une architecture d’exécution que prend en charge nommées threads, ou il peut être un nom dérivé le moteur de débogage. Vous pouvez également le nom du thread peut être défini par un appel à la [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)