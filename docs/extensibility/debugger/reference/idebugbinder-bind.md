---
title: IDebugBinder::Bind - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a783025c96053a89956a1c77d46b5e417938a2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736021"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Cette méthode obtient le contexte de mémoire ou l’objet qui contient la valeur actuelle du symbole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`pContainer`\
[dans] [L’IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui contient l’enfant référencé par `pField`.

`pField`\
[dans] [L’IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le symbole.

`ppObject`\
[out] Retourne `IDebugObject` le qui représente l’exemple du symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
