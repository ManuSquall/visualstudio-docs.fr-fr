---
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
ms.openlocfilehash: a9b9e2fa8f636581572b97da58fb9ddefeafd375
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892539"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’interface passée `pSession` est traitée uniquement comme un cookie, valeur qui identifie de façon unique le gestionnaire de débogage de session attaché à ce processus ; aucune des méthodes sur l’interface fournie n’est fonctionnelle.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
