---
title: IDebugPortEx2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2
helpviewer_keywords: IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06eab3133669381d13416c0990370ad01378222c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2"></a>IDebugPortEx2
Cette interface permet à la session de débogage manager (SDM) contrôle les programmes et les processus qui s’exécutent sur un port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface sur le même objet qui implémente [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Les appels SDM [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugPort2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPortEx2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Lance un fichier exécutable.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reprend l’exécution d’un processus.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Détermine si un processus peut être arrêté.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Arrête un processus.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtient l’ID de processus du port lui-même.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtient un programme associé à un nœud du programme.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface est normalement privée entre le SDM et le fournisseur de port personnalisé.  
  
 Si vous le souhaitez, un moteur de débogage (DE) pouvez rechercher cette interface le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface passé à [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) et utiliser [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) pour lancer le programme. Cela n’est pas obligatoire, toutefois, et un DE faire tout ce qui doit être fait pour lancer le programme de la demande.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)