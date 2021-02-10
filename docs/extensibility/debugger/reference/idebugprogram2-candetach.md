---
title: 'IDebugProgram2 :: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaff16923023598793dfdf9200105cc6b158ccb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936130"
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
