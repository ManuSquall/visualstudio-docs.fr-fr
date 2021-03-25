---
description: Cette méthode obtient un objet IDebugFunctionObject utilisé pour créer des paramètres de fonction.
title: 'IDebugBinder :: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bbcb8dba1593de824a5a0bb2d4d31f7602eb879
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067463"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Cette méthode obtient un objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilisé pour créer des paramètres de fonction.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Paramètres
`ppFunction`\
à Retourne l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilisée pour créer des paramètres de fonction.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
