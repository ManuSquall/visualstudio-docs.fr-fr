---
description: Demande que le programme arrête l’exécution la prochaine fois qu’un de ses threads tente de s’exécuter.
title: 'IDebugProgram2 :: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64ad2a22a06cc18595aabb37e3c244c7ea0c0be1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076158"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Demande que le programme arrête l’exécution la prochaine fois qu’un de ses threads tente de s’exécuter.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un événement [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque le programme tente ensuite d’exécuter du code après l’appel de cette méthode.

 Cette méthode est asynchrone en ce que la méthode retourne immédiatement une valeur sans nécessairement attendre l’arrêt du programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
