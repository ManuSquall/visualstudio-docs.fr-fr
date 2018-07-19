---
title: IDebugProcessEx2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 479206b75325c1b7e6bba0e4cc4e9b53944d73d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119160"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Cette interface permet à la session de débogage responsable de notifier un processus qu’elle est de s’attacher à ou de détachement d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que le [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) de l’interface :  
  
-   Suivi de prise en charge des sessions connectées à un processus  
  
-   Prise en charge attachement automatique entre plusieurs moteurs de débogage  
  
 Le fournisseur de port personnalisé peut implémenter cette interface si elle choisit.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
  
-   Les appels SDM [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProcess2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcessEx2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attacher](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informe le processus qu’une session de débogage maintenant le processus.|  
|[Détacher](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informe le processus qu’une session de débogage n’est plus le processus.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Ajoute des nœuds de programme pour obtenir la liste des moteurs de débogage.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est privée entre le SDM et le processus.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)