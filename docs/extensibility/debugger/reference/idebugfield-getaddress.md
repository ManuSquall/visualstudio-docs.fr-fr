---
description: Cette méthode obtient l’adresse de débogage d’un champ.
title: 'IDebugField :: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06b6d1770e5fa4c4d2548e0551c437b04e91feb2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077120"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Cette méthode obtient l’adresse de débogage d’un champ.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddress( 
   IDebugAddress** ppAddress
);
```

```csharp
int GetAddress(
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Paramètres
`ppAddress`\
à Retourne l’adresse en tant qu’objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
