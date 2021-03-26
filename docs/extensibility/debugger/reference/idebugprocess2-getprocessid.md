---
description: Obtient le GUID pour ce processus.
title: 'IDebugProcess2 :: GetProcessID, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b42b6f029ee6bbffdb1c59c55a2781d87d450d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081748"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Obtient le GUID pour ce processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Paramètres
`pguidProcessId`\
à Retourne le GUID de ce processus.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’identificateur global unique (GUID) identifie ce processus à partir de tous les autres processus en cours d’exécution dans le système.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
