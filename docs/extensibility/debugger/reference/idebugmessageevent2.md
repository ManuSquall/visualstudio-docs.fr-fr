---
title: IDebugMessageEvent2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Cette interface est utilisée par le moteur de débogage (DE) pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
 L’implémentation de cette interface doit communiquer l’appel de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) pour le DE. Par exemple, cela peut être fait avec un message publié au message de la DE la gestion des threads, ou l’objet qui implémente cette interface peut contenir une référence à la DE et rappeler le DE avec la réponse passée dans `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour afficher un message à l’utilisateur qui requiert une réponse. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugMessageEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtient le message à afficher.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Définit la réponse, le cas échéant, à partir de la boîte de message.|  
  
## <a name="remarks"></a>Notes  
 Le D’utilisera cette interface s’il requiert une réponse spécifique à partir de l’utilisateur pour un message particulier. Par exemple, si le D’Obtient un message « Accès refusé » après une tentative de se connecter à distance à un programme, le D’envoie ce message particulier à Visual Studio dans un `IDebugMessageEvent2` événement avec le style de boîte de message `MB_RETRYCANCEL`. Cela permet à l’utilisateur à réessayer ou annuler l’opération d’attachement.  
  
 Le DE spécifie comment ce message doit être gérée en suivant les conventions de la fonction Win32 `MessageBox` (consultez [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) pour plus d’informations).  
  
 Utilisez le [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interface pour envoyer des messages à Visual Studio qui ne nécessitent pas une réponse de l’utilisateur.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)