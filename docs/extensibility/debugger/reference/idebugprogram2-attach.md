---
description: Attache au programme.
title: 'IDebugProgram2 :: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f9565ea0975e38ced80f0747560cf1a24b4150c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076223"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Attache au programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Paramètres
`pCallback`\
dans Objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour la notification d’événements de débogage.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant présente certains codes d’erreur possibles.

|Valeur|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le programme spécifié est déjà attaché au débogueur.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite pendant la procédure d’attachement.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programme de bureau ne peut pas être attaché au débogueur.|

## <a name="remarks"></a>Notes
 Un moteur de débogage (DE) n’appelle jamais cette méthode pour effectuer un attachement à un programme. Si le DE s’exécute dans l’espace d’adressage du programme, la méthode [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) est appelée. Si le DE s’exécute dans l’espace d’adressage du gestionnaire de débogage de session (SDM), la méthode d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
