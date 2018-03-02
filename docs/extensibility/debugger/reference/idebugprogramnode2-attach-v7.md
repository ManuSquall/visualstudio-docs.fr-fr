---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7db57be153634476b8c0ba5ff6b6b1273ef190be
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> DÉCONSEILLÉE. N’UTILISEZ PAS.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>Paramètres

`pMDMProgram` [in] Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface qui représente le programme à attacher.

 `pCallback` [in] Le [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interface à utiliser pour envoyer des événements de débogage pour le SDM.

 `dwReason` [in] Une valeur à partir de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) énumération qui spécifie la raison de l’attachement.

## <a name="return-value"></a>Valeur de retour

Une implémentation doit toujours renvoyer `E_NOTIMPL`.

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`. Consultez le [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) si le nœud du programme doit indiquer qu’il ne peut pas être attaché à ou si le nœud de programme définit simplement le programme d’interface pour une autre approche `GUID`. Sinon, mettre en œuvre la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).

## <a name="prior-to-visual-studio-2005"></a>Avant Visual Studio 2005

Cette méthode doit être implémentée uniquement si le DE s’exécute dans l’espace d’adressage du programme en cours de débogage. Sinon, cette méthode doit retourner `S_FALSE`.

Lorsque cette méthode est appelée, le DE doit envoyer le [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objet d’événement, si elle n’a pas encore été envoyée pour cette instance de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface, ainsi que le [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objets d’événements. Le [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) objet d’événement est ensuite envoyé si la `dwReason` paramètre est `ATTACH_REASON_LAUNCH`.

Le DE doit appeler le [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet fourni par le [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événements de l’objet et doit stocker les GUID de ce programme dans les données d’instance pour le `IDebugProgram2` objet implémenté par le DE.

## <a name="see-also"></a>Voir aussi

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)