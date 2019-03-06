---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f626005621604d367f5878e36899aa2ff46114ee
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678447"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informe un moteur de débogage (dé) que le programme spécifié a été arrêté anormalement, et que l’Allemagne doit nettoyer toutes les références au programme et envoi d’un programme détruire des événements.

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

#### <a name="parameters"></a>Paramètres
 `pProgram`

 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme s’est terminé anormalement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une fois que cette méthode est appelée, l’Allemagne envoie par la suite un [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) événement le Gestionnaire de session de débogage (SDM).

 Cette méthode n’est pas implémentée (retourne `E_NOTIMPL`) si le DE s’exécute dans le même processus que le programme en cours de débogage. Cette méthode est implémentée uniquement si le DE s’exécute dans le même processus que le SDM.

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)