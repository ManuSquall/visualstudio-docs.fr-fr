---
description: Cette méthode obtient le contexte ou l’objet de la mémoire qui contient la valeur actuelle du symbole.
title: 'IDebugBinder :: bind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c373fbdae030de30544c67c1509eb812b746b7f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143655"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Cette méthode obtient le contexte ou l’objet de la mémoire qui contient la valeur actuelle du symbole.

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
dans [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui contient l’enfant référencé par `pField` .

`pField`\
dans [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le symbole.

`ppObject`\
à Retourne le `IDebugObject` qui représente l’instance du symbole.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
