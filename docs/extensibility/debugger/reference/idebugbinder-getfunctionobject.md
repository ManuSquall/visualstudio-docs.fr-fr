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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9868edafb18a129d119a818d9e51363d4964afa2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143648"
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
