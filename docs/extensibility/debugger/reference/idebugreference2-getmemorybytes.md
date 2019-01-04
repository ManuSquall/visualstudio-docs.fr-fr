---
title: IDebugReference2::GetMemoryBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d61334699b088a780c127a6e42abdff0636ebeb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887316"
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
Obtient les octets de mémoire qui contient physiquement la valeur d’une référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppMemoryBytes`  
 [out] Retourne un [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objet qui peut être utilisée pour récupérer la mémoire qui contient la valeur de la référence.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)