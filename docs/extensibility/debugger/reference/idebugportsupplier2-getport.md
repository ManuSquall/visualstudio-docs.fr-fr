---
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65b2d8264ef75c46de32ee65d994794d526c7ddb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693059"
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

#### <a name="parameters"></a>Paramètres
 `guidPort`

 [in] Identificateur global unique (GUID) du port.

 `ppPort`

 [out] Retourne un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objet qui représente le port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_PORTSUPPLIER_NO_PORT` si aucun port n’existe avec l’identificateur donné.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)