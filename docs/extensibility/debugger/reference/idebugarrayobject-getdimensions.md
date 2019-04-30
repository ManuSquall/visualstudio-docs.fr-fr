---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96079e3f82fccc958cc4b9123f8af4227393845f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923778"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient les dimensions du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
