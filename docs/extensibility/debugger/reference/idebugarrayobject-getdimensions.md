---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781da7eadce78d5332befe91231131f02341574b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319004"
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

## <a name="parameters"></a>Paramètres
`dwCount`\
[in] Le nombre de dimensions à récupérer.

`dwDimensions`\
[in, out] Un tableau est rempli avec les tailles de chaque dimension. `dwCount` Spécifie la taille maximale de la `dwDimensions` tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un tableau multidimensionnel peut avoir des tailles différentes pour chaque dimension. Par exemple, étant donné le tableau tridimensionnel `myarray[3][2][6]`, cette méthode retourne 3, 2 et 6 dans la `dwDimensions` paramètre dans cet ordre.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)