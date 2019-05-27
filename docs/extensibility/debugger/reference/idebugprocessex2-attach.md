---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edb130496f2896fc0678e850163cbc96ce321048
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199050"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Cette méthode informe le processus qu’une session est débogage maintenant le processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Paramètres
`pSession`\
[in] Une valeur qui identifie de façon unique la session attachement à ce processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’interface passée dans `pSession` doit être traité uniquement en tant que cookie, une valeur qui identifie de façon unique le Gestionnaire de débogage de session attachement à ce processus ; aucune des méthodes sur l’interface fournie sont fonctionnels.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)