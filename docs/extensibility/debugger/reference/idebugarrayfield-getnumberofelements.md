---
title: IDebugArrayField::GetNumberOfElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a228c0f9a213ecd12cafe09460288c1b60c333e3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985066"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Obtient le nombre d’éléments contenus dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwNumElements`  
 [out] Retourne le nombre d’éléments dans le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée est le nombre total d’éléments dans le tableau, quel que soit le nombre de dimensions.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)