---
title: 'IDebugBinder3 :: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735860"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Cette méthode localise un alias en fonction d’un nom. Cette opération recherche tous les alias dans le programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
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
