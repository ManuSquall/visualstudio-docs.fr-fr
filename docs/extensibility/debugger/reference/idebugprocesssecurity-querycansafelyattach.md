---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 891a0c200b02f8768ef68d1d87649bfd35cf59d2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040609"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Cette méthode permet le fournisseur de port afficher un avertissement avant que l’utilisateur joint à un processus non sécurisé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valeur de retour
 Les valeurs de retour sont comme suit :

- `S_OK`: Attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement n’est affiché.

- `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.

- `FAILURE`: Échec de l’attachement au processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)