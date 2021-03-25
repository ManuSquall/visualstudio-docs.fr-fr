---
description: Récupère un fournisseur de port spécifique.
title: 'IDebugCoreServer2 :: GetPortSupplier | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPortSupplier
helpviewer_keywords:
- IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e2cc718cc3f8ac99563881801fa3cd0565820c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077822"
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Récupère un fournisseur de port spécifique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortSupplier( 
   REFGUID               guidPortSupplier,
   IDebugPortSupplier2** ppPortSupplier
);
```

```csharp
int GetPortSupplier( 
   ref Guid                guidPortSupplier,
   out IDebugPortSupplier2 ppPortSupplier
);
```

## <a name="parameters"></a>Paramètres
`guidPortSupplier`\
dans GUID du fournisseur de ports à récupérer.

`ppPortSupplier`\
à Retourne un objet [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) représentant le fournisseur de ports souhaité.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
