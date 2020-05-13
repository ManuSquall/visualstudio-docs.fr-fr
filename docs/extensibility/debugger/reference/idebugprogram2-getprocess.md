---
title: IDebugProgram2::GetProcess Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722785"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtenez le processus dans lequel ce programme est en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Paramètres
`ppProcess`\
[out] Retourne l’interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 À moins qu’un moteur débagé (DE) ne implémente l’interface [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) la mise en œuvre de cette méthode par le DE devrait toujours revenir `E_NOTIMPL` parce qu’un DE ne peut pas déterminer dans quel processus il fonctionne et ne peut donc pas satisfaire à une mise en œuvre de cette méthode.

 La mise `IDebugEngineLaunch2` en œuvre de l’interface signifie que le DE doit savoir comment créer un processus; par conséquent, la mise en œuvre par le DE de l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) est en mesure de savoir dans quel processus il fonctionne.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
