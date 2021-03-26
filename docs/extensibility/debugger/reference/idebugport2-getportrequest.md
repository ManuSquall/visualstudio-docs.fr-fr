---
description: Obtient la description d’un port qui a été précédemment utilisé pour créer le port (si disponible).
title: 'IDebugPort2 :: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087481"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtient la description d’un port qui a été précédemment utilisé pour créer le port (si disponible).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Paramètres
`ppRequest`\
à Retourne un objet [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) représentant la requête utilisée pour créer le port.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  Retourne `E_PORT_NO_REQUEST` si un port n’a pas été créé à l’aide d’une demande de port [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
