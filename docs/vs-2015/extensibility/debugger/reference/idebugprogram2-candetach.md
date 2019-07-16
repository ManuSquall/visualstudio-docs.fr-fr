---
title: IDebugProgram2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a7f8bbabbba54cc7705aedc6e7f12ca1bffc924
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187927"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Détermine si un moteur de débogage (dé) pouvez détacher du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valeur de retour
 Si détacher, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `S_FALSE` si le D’Impossible de détacher du programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)