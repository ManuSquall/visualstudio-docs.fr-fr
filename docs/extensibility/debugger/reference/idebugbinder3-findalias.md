---
description: Cette méthode localise un alias en fonction d’un nom.
title: 'IDebugBinder3 :: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9958c1c2b93d6547f1f3453bafc9e331f9061844
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089054"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Cette méthode localise un alias en fonction d’un nom. Cette opération recherche tous les alias dans le programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Paramètres
`pcstrName`\
dans Nom de l’alias à rechercher.

`ppAlias`\
à Alias trouvé (le cas échéant) représenté par l’interface [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` (si l’alias est introuvable) ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode initialise l’objet de destination à la valeur null avant d’appeler ; Il teste ensuite une valeur NULL par la suite pour déterminer si l’alias a été trouvé ou non.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
