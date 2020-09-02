---
title: 'IEnumDebugPortSuppliers2 :: suivant | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2e887c6e00587c4101c73c9cc6b5bdd0a47789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164705"
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne l'ensemble d'éléments suivants de l'énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   IDebugPortSupplier2** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                  celt,  
   IDebugPortSupplier2[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre d'éléments à récupérer. Spécifie également la taille maximale du `rgelt` tableau.  
  
 `rgelt`  
 [in, out] Tableau d’éléments [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) à remplir.  
  
 `pceltFetched`  
 à Retourne le nombre d’éléments réellement retournés dans `rgelt` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si un nombre inférieur au nombre d’éléments demandés peut être retourné ; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
