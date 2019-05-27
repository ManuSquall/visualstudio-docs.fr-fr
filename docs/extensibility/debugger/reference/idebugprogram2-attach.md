---
title: IDebugProgram2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5e6debcc761872295e21dd17023d24429870e02
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200432"
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
[in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à utiliser pour la notification d’événement de débogage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant présente certains codes d’erreur possibles.

|Value|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le programme spécifié est déjà attaché au débogueur.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite lors de la procédure d’attachement.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programme de bureau ne peut pas être attaché au débogueur.|

## <a name="remarks"></a>Notes
 Un moteur de débogage (dé) n’appelle jamais cette méthode pour attacher à un programme. Si le dé s’exécute dans l’espace d’adressage du programme, le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode est appelée. Si l’espace d’adressage DE s’exécute dans le Gestionnaire de débogage de session (SDM) le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)