---
title: IDebugProcessSecurity::QueryCanSafelyAttach (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723201"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Cette méthode permet au fournisseur de port d’afficher un avertissement avant que l’utilisateur ne se fixe à un processus dangereux.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valeur de retour
 Les valeurs de rendement sont les suivantes :

- `S_OK`: L’attachement au processus est sans danger et aucune boîte de dialogue d’avertissement n’est affichée.

- `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement est montrée.

- `FAILURE`: L’attachement au processus échoue.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
