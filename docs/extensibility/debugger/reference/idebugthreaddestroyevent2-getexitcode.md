---
title: 'IDebugThreadDestroyEvent2 :: GetExitCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugThreadDestroyEvent2::GetExitCode
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 567e7fdedbf408ce9cac137f2b240626fd16d10c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940226"
---
# <a name="idebugthreaddestroyevent2getexitcode"></a>IDebugThreadDestroyEvent2::GetExitCode
Obtient le code de sortie d’un thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExitCode ( 
   DWORD* pdwExit
);
```

```csharp
int GetExitCode ( 
   out uint pdwExit
);
```

## <a name="parameters"></a>Paramètres
`pdwExit`\
à Retourne le code de sortie du thread.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)
