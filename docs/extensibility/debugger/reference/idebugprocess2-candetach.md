---
description: Détermine si le gestionnaire de débogage de session (SDM) peut détacher le processus.
title: 'IDebugProcess2 :: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e876d5642cf8a4b7b60f5119839e64959f296e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151673"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Détermine si le gestionnaire de débogage de session (SDM) peut détacher le processus.

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
 En cas de réussite, retourne `S_OK.` `S_FALSE` la valeur si le débogueur ne peut pas détacher du processus. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
