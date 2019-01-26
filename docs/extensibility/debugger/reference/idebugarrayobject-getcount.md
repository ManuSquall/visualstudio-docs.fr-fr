---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0058599a6f7967aa96490223de519b69710242ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023000"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtient le nombre d’éléments dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwElements`  
 [out] Retourne le nombre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode voit tous les éléments d’un objet tableau comme un tableau unidimensionnel, même si l’objet de tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]`, cette méthode retourne 36 dans le `pdwElements` paramètre. Utilisez le [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) méthode pour récupérer les éléments individuels d’un à la fois.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)