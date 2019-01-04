---
title: IDebugArrayObject::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e433b8c50b363347469586d2ecde4bd287a58264
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857283"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtient le rang du tableau, autrement dit, le nombre de dimensions.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwRank`  
 [out] Retourne le rang.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) méthode pour récupérer la taille de chaque dimension de l’objet de tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)