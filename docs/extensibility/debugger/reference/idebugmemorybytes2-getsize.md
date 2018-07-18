---
title: IDebugMemoryBytes2::GetSize | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fce2d9beecb6c2a51d64e229dcf386795ab55f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111275"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Récupère la taille, en octets, de la mémoire représentée par ce [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pqwSize`  
 [out] Retourne la taille, en octets de l’espace de mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)