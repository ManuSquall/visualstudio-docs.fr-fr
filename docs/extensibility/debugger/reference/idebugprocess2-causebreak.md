---
description: Demande que le programme suivant qui exécute le code dans ce processus s’arrête et envoie un objet d’événement IDebugBreakEvent2.
title: 'IDebugProcess2 :: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c79fbc17f02a49a1bbab416473bb99e201c24526
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071673"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Demande que le programme suivant qui exécute le code dans ce processus s’arrête et envoie un objet d’événement [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) .

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

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
