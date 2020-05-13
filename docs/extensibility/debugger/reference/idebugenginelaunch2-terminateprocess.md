---
title: IDebugEngineLaunch2::TerminateProcess (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::TerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::TerminateProcess
ms.assetid: f7039e7f-5f57-4222-9ad2-11a66b2da6e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971259edc89d1ad8be01b6e6e4db46f760534349
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730512"
---
# <a name="idebugenginelaunch2terminateprocess"></a>IDebugEngineLaunch2::TerminateProcess
Termine un processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int TerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Paramètres
`pProcess`\
[dans] Un objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus à mettre fin.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez la méthode [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md) avant d’appeler cette méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)
