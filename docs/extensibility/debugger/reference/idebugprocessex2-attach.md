---
description: Cette méthode informe le processus qu’une session est en train de déboguer le processus.
title: 'IDebugProcessEx2 :: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149741"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Cette méthode informe le processus qu’une session est en train de déboguer le processus.

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
dans Valeur qui identifie de façon unique la session attachée à ce processus.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’interface passée `pSession` est traitée uniquement comme un cookie, valeur qui identifie de façon unique le gestionnaire de débogage de session attaché à ce processus ; aucune des méthodes sur l’interface fournie n’est fonctionnelle.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
