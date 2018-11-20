---
title: IDebugProcessEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b6b98d6b1f95171d4efb1e0d4bed040d9c1482d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721485"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface permet à la session de débogage manager (SDM) notifier un processus qu’il est d’attachement à ou de détachement d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que le [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) de l’interface :  
  
- Suivi de prise en charge des sessions connectées à un processus  
  
- Prise en charge l’attachement automatique entre plusieurs moteurs de débogage  
  
  Le fournisseur de port personnalisé peut implémenter cette interface si elle choisit.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
  
-   Les appels SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un `IDebugProcess2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcessEx2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attacher](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informe le processus qu’une session est débogage maintenant le processus.|  
|[Détacher](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informe le processus qu’une session est le débogage n’est plus le processus.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Ajoute des nœuds de programme pour obtenir la liste de moteurs de débogage.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est privée entre le SDM et le processus.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

