---
title: IDebugMemoryContext2::Subtract | Microsoft Docs
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
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bb2ce49440d5a2196b983ea53c761496a2c4570
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284867"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Soustrait la valeur spécifiée à partir du contexte actuel et retourne un nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [out] Retourne un nouvel [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un contexte de mémoire étant une adresse, en soustrayant une valeur à partir d’une adresse génère une nouvelle adresse qui requiert une nouvelle interface de contexte.  
  
 Cette méthode doit produire toujours un nouveau contexte, même si l’adresse obtenue est en dehors de l’espace de mémoire associé à ce contexte. La seule exception est si aucune mémoire ne pouvant être allouée pour le nouveau contexte ou si `ppMemCxt` est une valeur null (qui est une erreur).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

