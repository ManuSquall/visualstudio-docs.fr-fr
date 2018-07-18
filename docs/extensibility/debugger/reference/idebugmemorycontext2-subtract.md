---
title: IDebugMemoryContext2::Subtract | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6cc7265def2d1a4b184f27865461706e62b98f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113635"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Soustrait la valeur spécifiée à partir du contexte actuel et retourne un nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCount`  
 [in] Le nombre d’octets de mémoire à décrémenter.  
  
 `ppMemCxt`  
 [out] Retourne un nouveau [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un contexte de la mémoire est une adresse, afin de la soustraction d’une valeur à partir d’une adresse génère une nouvelle adresse qui requiert une nouvelle interface de contexte.  
  
 Cette méthode doit produire toujours d’un nouveau contexte, même si l’adresse obtenue est en dehors de l’espace de mémoire associé à ce contexte. La seule exception est si aucune mémoire ne pouvant être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur null (qui est une erreur).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)