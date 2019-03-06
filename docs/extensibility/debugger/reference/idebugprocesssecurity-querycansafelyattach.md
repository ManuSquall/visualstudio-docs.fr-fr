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
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701431"
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

-   `S_OK`: Attachement au processus est sécurisé et aucune boîte de dialogue d’avertissement n’est affiché.

-   `S_FALSE`: L’attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement s’affiche.

-   `FAILURE`: Échec de l’attachement au processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)