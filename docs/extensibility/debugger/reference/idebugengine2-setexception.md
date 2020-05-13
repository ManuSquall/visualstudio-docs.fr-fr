---
title: IDebugEngine2:SetException (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7398db3c15c58821e05eff839a1022276401d569
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730936"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Précise comment le moteur de débogé (DE) doit gérer une exception donnée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Paramètres
`pException`\
[dans] Une structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) qui décrit l’exception et comment la déboiffer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un DE pourrait être chargé d’arrêter le programme générant une exception à la première chance, la deuxième chance, ou pas du tout.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
