---
description: Récupère une interface de code managé qui représente la valeur associée à cet alias.
title: 'IDebugAlias :: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b809e16fefb9306da842f39d93bdb3dd0f7b404f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143933"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Récupère une interface de code managé qui représente la valeur associée à cet alias.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Paramètres
`ppUnk`\
[out] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour l' `ICorDebugValue` interface.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode s’applique uniquement aux valeurs managées ( `ICorDebugValue` est une interface disponible dans le .NET Framework et est définie dans le kit de développement logiciel (SDK) .NET Framework dans le fichier Cordebug. idl).

## <a name="see-also"></a>Voir aussi
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
