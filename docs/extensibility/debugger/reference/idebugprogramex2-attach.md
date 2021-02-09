---
title: 'IDebugProgramEx2 :: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30818627f8ebc293e444b43adb0590db077da4a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898830"
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
dans Objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui représente la fonction de rappel à laquelle le moteur de débogage attaché envoie des événements.

`dwReason`\
dans Valeur de l’énumération [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui décrit la raison de l’opération d’attachement.

`pSession`\
dans Valeur qui identifie de façon unique la session qui est attachée au programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur. Cette méthode doit retourner `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si le programme est déjà attaché.

## <a name="remarks"></a>Remarques
 Le port qui contient le programme peut utiliser la valeur dans `pSession` pour déterminer la session qui tente de s’attacher au programme. Par exemple, si un port n’autorise qu’une seule session de débogage à s’attacher à un processus à la fois, le port peut déterminer si la même session est déjà attachée à d’autres programmes dans le processus.

> [!NOTE]
> L’interface passée `pSession` est traitée uniquement comme un cookie, valeur qui identifie de façon unique le gestionnaire de débogage de session attaché à ce programme ; aucune des méthodes sur l’interface fournie n’est fonctionnelle.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
