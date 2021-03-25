---
description: Détermine si un moteur de débogage (DE) peut se détacher du programme.
title: 'IDebugProgram2 :: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e751429fe26060a515f94aa3d402954ff598d39
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076171"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Détermine si un moteur de débogage (DE) peut se détacher du programme.

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
 Si peut détacher, retourne `S_OK` ; sinon, retourne un code d’erreur. Retourne `S_FALSE` si le ne peut pas se détacher du programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
