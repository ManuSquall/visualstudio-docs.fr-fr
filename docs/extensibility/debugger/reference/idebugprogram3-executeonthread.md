---
title: IDebugProgram3::ExecuteOnThread (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722661"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Exécute le programme de débbugger. Le thread est retourné pour donner aux informations de débbugger sur le thread que l’utilisateur consulte lors de l’exécution du programme.

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
[dans] Un objet [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il existe trois façons différentes pour un débbugeur de reprendre l’exécution après l’arrêt :

- Exécuter: Annuler toute étape précédente, et exécuter jusqu’à la prochaine période d’arrêt et ainsi de suite.

- Étape : Annulez n’importe quelle vieille étape, et exécutez jusqu’à ce que la nouvelle étape se termine.

- Continuer: Courir à nouveau, et laisser toute vieille étape active.

  Le thread `ExecuteOnThread` passé est utile pour décider quelle étape annuler. Si vous ne connaissez pas le thread, exécuter exécute annule toutes les étapes. Avec la connaissance du thread, vous n’avez qu’à annuler l’étape sur le fil actif.

## <a name="see-also"></a>Voir aussi
- [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
