---
title: IDebugProgram2::GetMemoryBytes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 289a1f7e2802fcf8187f74ec803af71cfb4a6bc0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115913"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Récupère les octets de mémoire occupées par le programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppMemoryBytes`  
 [out] Retourne un [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objet qui représente les octets de mémoire du programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les octets de mémoire, tel que représenté par la [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objet est utilisé dans l’image du programme en mémoire et pas de mémoire qui a été alloué lorsque le programme a été exécuté.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)