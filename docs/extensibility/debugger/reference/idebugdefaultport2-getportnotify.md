---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7e0cc45ba3f692f799deb568bcbb84cc5edf7bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921807"
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

#### <a name="parameters"></a>Paramètres
 `ppPortNotify`

 [out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Normalement, le `QueryInterface` méthode est appelée sur l’objet qui implémente le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface pour obtenir un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface. Toutefois, il existe des circonstances dans lesquelles l’interface souhaitée est implémentée sur un autre objet. Cette méthode masque ces circonstances et retourne le `IDebugPortNotify2` interface à partir de l’objet le plus approprié.

## <a name="see-also"></a>Voir aussi
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)