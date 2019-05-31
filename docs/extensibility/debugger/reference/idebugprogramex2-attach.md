---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db27f29b37480081d29e452d74a6da0c5cea59a6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325186"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Attacher une session à un programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Paramètres
`pCallback`\
[in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet qui représente la fonction de rappel qui envoie les événements vers le moteur de débogage attaché.

`dwReason`\
[in] Une valeur comprise entre le [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) énumération qui décrit la raison de l’opération d’attachement.

`pSession`\
[in] Une valeur qui identifie de façon unique la session concerne l’attachement au programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Cette méthode doit retourner `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si le programme est déjà attaché.

## <a name="remarks"></a>Notes
 Le port qui contient le programme peut utiliser la valeur dans `pSession` pour déterminer quelle session tente de se joindre au programme. Par exemple, si un port autorise la session de débogage qu’une seule s’attacher à un processus à la fois, le port peut déterminer si la même session est déjà attachée à d’autres programmes dans le processus.

> [!NOTE]
> L’interface passée dans `pSession` doit être traité uniquement en tant que cookie, une valeur qui identifie de façon unique le Gestionnaire de débogage de session attachement à ce programme ; aucune des méthodes sur l’interface fournie sont fonctionnels.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)