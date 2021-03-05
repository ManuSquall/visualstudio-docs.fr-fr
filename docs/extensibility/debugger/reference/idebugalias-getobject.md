---
description: Obtient l’objet pour lequel cet alias est destiné.
title: 'IDebugAlias :: GetObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10bcb0bb356907cb3f23b1c470248b9926f329ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143894"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Obtient l’objet pour lequel cet alias est destiné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetObject(
   IDebugObject2** ppObject
);
```

```csharp
int GetObject(
   Out IDebugObject2 ppObject
)
```

## <a name="parameters"></a>Paramètres
`ppObject`\
à [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) représenté par cet alias.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
