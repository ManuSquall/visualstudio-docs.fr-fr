---
description: Cette interface est utilisée par le moteur de débogage (DE) pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5593e822b974ddb7c666f622192e3e4630b7222
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058428"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Cette interface est utilisée par le moteur de débogage (DE) pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur.

## <a name="syntax"></a>Syntaxe

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface.

 L’implémentation de cette interface doit communiquer l’appel de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) de Visual Studio à l’de. Par exemple, cette opération peut être effectuée avec un message publié dans le thread DE gestion des messages de, ou l’objet qui implémente cette interface peut contenir une référence à l’de et rappeler à l’à l’aide de la réponse passée dans `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour afficher un message à l’utilisateur qui requiert une réponse. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugMessageEvent2` .

|Méthode|Description|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtient le message à afficher.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Définit la réponse, le cas échéant, dans la boîte de message.|

## <a name="remarks"></a>Notes
 Le DE utilise cette interface s’il requiert une réponse spécifique de l’utilisateur pour un message particulier. Par exemple, si le message DE obtient un message « accès refusé » après une tentative d’attachement à distance à un programme, le DE envoie ce message particulier à Visual Studio dans un `IDebugMessageEvent2` événement avec le style de la boîte de message `MB_RETRYCANCEL` . Cela permet à l’utilisateur de réessayer ou d’annuler l’opération d’attachement.

 Le DE spécifie comment ce message doit être traité en suivant les conventions de la fonction Win32 `MessageBox` (pour plus d’informations, consultez [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 Utilisez l’interface [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer des messages à Visual Studio qui ne nécessitent pas de réponse de l’utilisateur.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
