---
title: 'IDebugProcessSecurity :: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3f2c02610b5fbe99335ccea6d7c566a0fe58df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931459"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Cette méthode permet au fournisseur de port d’afficher un avertissement avant que l’utilisateur ne soit attaché à un processus non sécurisé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valeur de retour
 Les valeurs de retour sont les suivantes :

- `S_OK`: L’attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement ne s’affiche.

- `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.

- `FAILURE`: L’attachement au processus échoue.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
