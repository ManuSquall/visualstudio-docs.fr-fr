---
title: 'IDebugArrayField :: GetNumberOfElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3454624feab268af089a5e82e38c0cce3d23ab03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940304"
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
à Retourne le nombre d’éléments dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La valeur retournée est le nombre total d’éléments dans le tableau, quel que soit le nombre de dimensions.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
