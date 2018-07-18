---
title: IEnumDebugPortSuppliers2::Clone | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPortSuppliers2::Clone
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a197c5452d229528f5492ca38c8513817c23df73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123441"
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne une copie de cette énumération comme un objet distinct.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et l’original sont distincts et peuvent être modifiées individuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)