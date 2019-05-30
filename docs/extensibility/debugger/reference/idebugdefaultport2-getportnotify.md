---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd85f76ab0c882656ca79fe02296f30bdb83f523
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351762"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Cette méthode obtient un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface pour ce port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Paramètres
`ppPortNotify`\
[out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Normalement, le `QueryInterface` méthode est appelée sur l’objet qui implémente le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface pour obtenir un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface. Toutefois, il existe des circonstances dans lesquelles l’interface souhaitée est implémentée sur un autre objet. Cette méthode masque ces circonstances et retourne le `IDebugPortNotify2` interface à partir de l’objet le plus approprié.

## <a name="see-also"></a>Voir aussi
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)