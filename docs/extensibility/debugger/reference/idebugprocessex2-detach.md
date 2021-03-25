---
description: Cette méthode informe le processus qu’une session n’est plus en train de déboguer le processus.
title: IDebugProcessEx2 ::D Etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5ad25fe6461f1df89ada83623ab4e28194ca207
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076327"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Cette méthode informe le processus qu’une session n’est plus en train de déboguer le processus.

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

## <a name="parameters"></a>Paramètres
`pSession`\
dans Valeur qui identifie de façon unique la session à partir de laquelle détacher ce processus.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’interface passée `pSession` est traitée uniquement comme un cookie, valeur qui identifie de façon unique le gestionnaire de débogage de session qui a été attaché à l’origine à ce processus ; aucune des méthodes sur l’interface fournie n’est fonctionnelle.

## <a name="see-also"></a>Voir aussi
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
