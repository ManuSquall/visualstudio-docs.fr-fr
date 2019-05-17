---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e736c14b1a87188f45658a51cff0c123553332e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917500"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Cette méthode informe le processus qu’une session est le débogage n’est plus le processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

#### <a name="parameters"></a>Paramètres
 `pSession`

 [in] Une valeur qui identifie de façon unique la session pour détacher ce processus à partir de l’utilisateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’interface passée dans `pSession` est traité uniquement comme un cookie, une valeur qui identifie de façon unique le Gestionnaire de débogage de session qui a initialement attachée à ce processus ; aucune des méthodes sur l’interface fournie sont fonctionnels.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)