---
title: IDebugDisassemblyStream2::GetSize | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f43a0fe3d7d2ad7c54ee9203037595dade7c6486
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtient la taille dans les instructions de ce flux de code machine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pnSize`  
 [out] Retourne la taille, dans les instructions.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode peut être utilisée pour allouer un tableau de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structures qui est ensuite transmise à la [en lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [En lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)