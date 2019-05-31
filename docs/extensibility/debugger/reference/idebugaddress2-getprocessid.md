---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f363ba75d21b147eee6ad39276b949c703e932ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324463"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Récupère l’ID de processus qui possède l’objet représenté par ce [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interface.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Paramètres
`pProcID`\
[out] L’ID de processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)