---
title: 'IDebugPortSupplier2 :: AddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e126612ed8b081e5ba0b703d14399ac74d78a9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906303"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Ajoute un port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Paramètres
`pRequest`\
dans Objet [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port à ajouter.

`ppPort`\
à Retourne un objet [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) qui représente le port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Cette méthode crée en fait le port demandé et l’ajoute à la liste interne des ports actifs du fournisseur de port. La méthode [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) peut être appelée en premier pour éviter des retards fastidieux.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
