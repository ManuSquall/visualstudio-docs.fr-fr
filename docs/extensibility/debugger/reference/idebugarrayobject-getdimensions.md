---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b33df4ab74b0446b18f2c2a1693ffc8f711bb2fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955893"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Obtient les dimensions du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCount`  
 [in] Le nombre de dimensions à récupérer.  
  
 `dwDimensions`  
 [in, out] Un tableau est rempli avec les tailles de chaque dimension. `dwCount` Spécifie la taille maximale de la `dwDimensions` tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un tableau multidimensionnel peut avoir des tailles différentes pour chaque dimension. Par exemple, étant donné le tableau tridimensionnel `myarray[3][2][6]`, cette méthode retourne 3, 2 et 6 dans la `dwDimensions` paramètre dans cet ordre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)