---
title: IDebugCanStopEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2
helpviewer_keywords: IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 585e1c8760152c9c42e1950c45d3e3821bbe93df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Cette interface est utilisée pour demander le Gestionnaire de session de débogage (SDM) s’il faut arrêter à l’emplacement du code en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour prendre en charge le pas à pas détaillé dans le code source. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface).  
  
 L’implémentation de cette interface doit communiquer l’appel de la SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) pour le moteur de débogage. Par exemple, cela est possible avec un message publié sur le thread des messages du moteur de débogage ou de l’objet qui implémente cette interface peut contenir une référence au moteur de débogage et rappeler dans le moteur de débogage avec l’indicateur passé dans `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le DE peut envoyer cette méthode chaque fois que la D’est invitée à continuer l’exécution et DE est parcours du code. Cet événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugCanStopEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtient la raison de cet événement.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Spécifie si le programme en cours de débogage doit s’arrêter à l’emplacement de cet événement (et envoyer un événement qui décrit la raison de l’arrêt) ou simplement de poursuivre l’exécution.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtient le contexte de document qui décrit l’emplacement de cet événement.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtient le contexte de code qui décrit l’emplacement de cet événement.|  
  
## <a name="remarks"></a>Remarques  
 Le D’envoie cette interface si les étapes de l’utilisateur dans une fonction et DE ne recherche aucune information de débogage il ou les informations de débogage existent mais le DE ne sait pas si le code source peut être affiché pour cet emplacement.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)