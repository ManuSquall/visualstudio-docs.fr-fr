---
description: Récupère l’ID du processus qui possède l’objet représenté par cette interface IDebugAddress2.
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
ms.openlocfilehash: eeae55e91df8dac3fb176952a352df642facb055
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154949"
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
