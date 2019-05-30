---
title: IDebugArrayField::GetNumberOfElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e8576c7f7365f8f87f8b31a90e414b75000026d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321737"
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

## <a name="parameters"></a>Paramètres
`pdwNumElements`\
[out] Retourne le nombre d’éléments dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La valeur retournée est le nombre total d’éléments dans le tableau, quel que soit le nombre de dimensions.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)