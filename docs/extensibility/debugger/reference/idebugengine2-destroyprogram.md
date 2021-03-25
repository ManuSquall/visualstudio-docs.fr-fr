---
description: Informe un moteur de débogage (DE) que le programme spécifié a été arrêté de manière atypique et que le DE doit nettoyer toutes les références au programme et envoyer un événement de destruction du programme.
title: IDebugEngine2 ::D estroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0a58dd5893c3235ded9c7eeb5f5d47e3ddcb380
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093845"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informe un moteur de débogage (DE) que le programme spécifié a été arrêté de manière atypique et que le DE doit nettoyer toutes les références au programme et envoyer un événement de destruction du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Paramètres
`pProgram`\
dans Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme qui s’est arrêté de façon inattendue.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une fois cette méthode appelée, la méthode DE envoie par la suite un événement [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) au gestionnaire de débogage de session (SDM).

 Cette méthode n’est pas implémentée (retourne `E_NOTIMPL` ) si le de s’exécute dans le même processus que le programme en cours de débogage. Cette méthode est implémentée uniquement si le DE s’exécute dans le même processus que le SDM.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
