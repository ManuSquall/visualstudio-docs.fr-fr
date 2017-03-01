---
title: IDebugMessageEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Cette interface est utilisée par le moteur de débogage (DE) pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le D’implémente cette interface pour envoyer un message à Visual Studio qui requiert une réponse de l’utilisateur. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
 L’implémentation de cette interface doit communiquer à l’appel de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) pour le DE. Par exemple, cela peut être fait avec un message publié à un message de la DE la gestion des threads, ou l’objet qui implémente cette interface peut contenir une référence à la DE et rappeler la DE la réponse transmise dans `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le DE crée et envoie cet objet d’événement pour afficher un message à l’utilisateur qui nécessite une réponse. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugMessageEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtient le message à afficher.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Définit la réponse, le cas échéant, à partir de la boîte de message.|  
  
## <a name="remarks"></a>Remarques  
 Le D’utilise cette interface s’il requiert une réponse de l’utilisateur spécifique pour un message particulier. Par exemple, si le DE reçoit un message « Accès refusé » après une tentative de se connecter à distance à un programme, le D’envoie ce message particulier à Visual Studio dans un `IDebugMessageEvent2` événement avec le style de boîte de message `MB_RETRYCANCEL`. Cela permet à l’utilisateur à réessayer ou à annuler l’opération d’attachement.  
  
 Le DE spécifie comment ce message doit être géré en suivant les conventions de la fonction Win32 `MessageBox` (voir [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) pour plus d’informations).  
  
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
