---
description: Cette méthode obtient une interface au serveur sur lequel se trouve ce port.
title: 'IDebugDefaultPort2 :: GetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d5bfd242cd3f441bf094f94e41a78e240f1ec46
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162977"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Cette méthode obtient une interface au serveur sur lequel se trouve ce port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Paramètres
`ppServer`\
à Retourne un objet implémentant l’interface [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) est implémenté par Visual Studio et représente le serveur sur lequel se trouve le port.

## <a name="see-also"></a>Voir aussi
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
