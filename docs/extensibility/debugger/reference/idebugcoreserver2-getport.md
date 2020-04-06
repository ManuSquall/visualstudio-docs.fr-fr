---
title: IDebugCoreServer2::GetPort - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8dfafffb485150687b1877295a00a8ec6b71cfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733110"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Récupère un port spécifique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Paramètres
`guidPort`\
[dans] GUID du port à récupérer.

`ppPort`\
[out] Retourne un objet [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) représentant le port désiré.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_PORTSUPPLIER_NO_PORT` s’il n’y a pas de port avec l’identifiant donné.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
