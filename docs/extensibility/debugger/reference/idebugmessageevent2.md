---
title: IDebugMessageEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727364"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Cette interface est utilisée par le moteur de débogé (DE) pour envoyer un message à Visual Studio qui nécessite une réponse de l’utilisateur.

## <a name="syntax"></a>Syntaxe

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour envoyer un message à Visual Studio qui nécessite une réponse de l’utilisateur. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

 La mise en œuvre de cette interface doit communiquer l’appel de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) à la DE. Par exemple, cela peut être fait avec un message posté sur le thread de traitement des messages de l’DE, ou l’objet de mise en œuvre de cette interface pourrait tenir une référence à la DE et rappeler à la DE avec la réponse passée dans `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour afficher un message à l’utilisateur qui nécessite une réponse. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugMessageEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtient le message à afficher.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Définit la réponse, le cas échéant, à partir de la boîte de message.|

## <a name="remarks"></a>Notes
 Le DE utilisera cette interface si elle nécessite une réponse spécifique de l’utilisateur pour un message particulier. Par exemple, si le DE reçoit un message "Access Denied" après une tentative de s’attacher `IDebugMessageEvent2` à distance à `MB_RETRYCANCEL`un programme, le DE envoie ce message particulier à Visual Studio dans un événement avec le style boîte de message . Cela permet à l’utilisateur de réessayer ou d’annuler l’opération de jointage.

 Le DE précise comment ce message doit être traité en suivant les `MessageBox` conventions de la fonction Win32 (voir [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) pour plus de détails).

 Utilisez l’interface [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer des messages à Visual Studio qui ne nécessitent pas de réponse de l’utilisateur.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
