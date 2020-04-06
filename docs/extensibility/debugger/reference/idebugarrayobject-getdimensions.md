---
title: IDebugArrayObject::GetDimensions - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 527f79724aeac0de58d0ae63c9c2408ed2eca9ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736164"
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
[dans] Le nombre de dimensions à récupérer.

`dwDimensions`\
[dans, dehors] Un tableau qui est rempli avec les tailles de chaque dimension. `dwCount`spécifie la `dwDimensions` taille maximale du tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Un tableau multidimensionnel peut avoir des tailles différentes pour chaque dimension. Par exemple, étant donné `myarray[3][2][6]`le tableau tridimensionnel, cette méthode retournerait `dwDimensions` 3, 2 et 6 dans le paramètre dans cet ordre.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
