---
description: Cette méthode obtient une interface IDebugPortNotify2 pour ce port.
title: 'IDebugDefaultPort2 :: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077471"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Cette méthode obtient une interface [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) pour ce port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Paramètres
`ppPortNotify`\
à Objet [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Normalement, la `QueryInterface` méthode est appelée sur l’objet implémentant l’interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) pour obtenir une interface [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Toutefois, dans certains cas, l’interface souhaitée est implémentée sur un objet différent. Cette méthode masque ces circonstances et retourne l' `IDebugPortNotify2` interface à partir de l’objet le plus approprié.

## <a name="see-also"></a>Voir aussi
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
