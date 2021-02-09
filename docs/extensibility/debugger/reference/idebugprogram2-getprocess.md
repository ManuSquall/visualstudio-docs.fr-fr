---
title: 'IDebugProgram2 :: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cd3b6e76a7e675a2228217d9a72c1d004de919c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891005"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtient le processus dans lequel ce programme s’exécute.

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
à Retourne l’interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 À moins qu’un moteur de débogage (DE) n’implémente l’interface [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , l’implémentation de de cette méthode doit toujours retourner, `E_NOTIMPL` car un de ne peut pas déterminer le processus dans lequel il s’exécute et, par conséquent, ne peut pas satisfaire à une implémentation de cette méthode.

 L’implémentation de l' `IDebugEngineLaunch2` interface signifie que le de doit savoir comment créer un processus ; par conséquent, l’implémentation de de l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) est en mesure de connaître le processus dans lequel elle s’exécute.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
