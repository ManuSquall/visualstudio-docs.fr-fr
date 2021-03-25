---
description: Désactive l’attachement automatique pour tous les moteurs de débogage associés à ce serveur.
title: IDebugCoreServer3 ::D isableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88f21dbed27b0ec525f127933cd9a5fc28ed5646
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077666"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
Désactive l’attachement automatique pour tous les moteurs de débogage associés à ce serveur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisableAutoAttach(
   void
);
```

```csharp
int DisableAutoAttach();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
