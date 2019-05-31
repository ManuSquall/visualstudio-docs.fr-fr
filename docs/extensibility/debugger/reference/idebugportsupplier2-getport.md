---
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b27c810ec6cb71cacb54e39ad97a95b53480232
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340145"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Obtient un port à partir d’un fournisseur de port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Paramètres
`guidPort`\
[in] Identificateur global unique (GUID) du port.

`ppPort`\
[out] Retourne un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objet qui représente le port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_PORTSUPPLIER_NO_PORT` si aucun port n’existe avec l’identificateur donné.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)