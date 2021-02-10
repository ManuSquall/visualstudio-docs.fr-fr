---
title: 'IDebugAddress2 :: GetProcessID, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 493f2476eef1cdb68f825240fa4b56779ef7a0d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944867"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Récupère l’ID du processus qui possède l’objet représenté par cette interface [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) .

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
à ID du processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
