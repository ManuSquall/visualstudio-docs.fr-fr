---
description: Spécifie comment le moteur DE débogage (DE) doit gérer une exception donnée.
title: 'IDebugEngine2 :: SetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a327620ed9eddbba71f84c9950185f7987e8a79
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087910"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Spécifie comment le moteur DE débogage (DE) doit gérer une exception donnée.

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
dans Structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) qui décrit l’exception et comment la déboguer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un peut être demandé d’arrêter le programme qui génère une exception à la première chance, la deuxième chance ou pas du tout.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
