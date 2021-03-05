---
description: Exécute le programme du débogueur.
title: 'IDebugProgram3 :: ExecuteOnThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3d996fd7b8cda1d5e36322c85d49c9889dd66dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146000"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Exécute le programme du débogueur. Le thread est retourné pour fournir les informations du débogueur sur le thread affiché par l’utilisateur lors de l’exécution du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Paramètres
`pThread`\
dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il existe trois façons différentes de reprendre l’exécution d’un débogueur après l’arrêt :

- Exécuter : annuler toute étape précédente et exécuter jusqu’au point d’arrêt suivant, et ainsi de suite.

- Étape : annulez toute ancienne étape et exécutez jusqu’à ce que la nouvelle étape soit terminée.

- Continuer : réexécutez et laissez l’ancienne étape active.

  Le thread passé à `ExecuteOnThread` est utile pour décider de l’étape à annuler. Si vous ne connaissez pas le thread, l’exécution de l’instruction EXECUTE Annule toutes les étapes. Avec la connaissance du thread, il vous suffit d’annuler l’étape sur le thread actif.

## <a name="see-also"></a>Voir aussi
- [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
