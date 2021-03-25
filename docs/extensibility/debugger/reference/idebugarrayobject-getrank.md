---
description: Obtient le rang du tableau, autrement dit le nombre de dimensions.
title: 'IDebugArrayObject :: GetRank, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1440ff2fa82c8296bf54b106b622556a8eebb611
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094326"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtient le rang du tableau, autrement dit le nombre de dimensions.

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

## <a name="parameters"></a>Paramètres
`pdwRank`\
à Retourne le rang.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Utilisez la méthode [GetDimensions,](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) pour récupérer la taille de chaque dimension de l’objet Array.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
