---
title: IDebugProgramEx2::Attach Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722380"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Joindre une session à un programme.

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
[dans] Un objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui représente la fonction de rappel que le moteur de débogé attaché envoie des événements.

`dwReason`\
[dans] Une valeur de [l’énumération ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui décrit la raison de l’opération de fixation.

`pSession`\
[dans] Une valeur qui identifie de façon unique la session qui s’attache au programme.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur. Cette méthode `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` doit revenir si le programme est déjà attaché.

## <a name="remarks"></a>Notes
 Le port qui contient le programme `pSession` peut utiliser la valeur pour déterminer quelle session tente de s’attacher au programme. Par exemple, si un port permet à une seule session de débaillement de s’attacher à un processus à la fois, le port peut déterminer si la même session est déjà rattachée à d’autres programmes du processus.

> [!NOTE]
> L’interface `pSession` passée est d’être traitée uniquement comme un cookie, une valeur qui identifie uniquement le gestionnaire de débogé de session attaché à ce programme; aucune des méthodes sur l’interface fournie n’est fonctionnelle.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
