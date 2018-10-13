---
title: IDebugProgram3 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ea0f1412ca45ae59ea50555d70a7130b2e99f42
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295436"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un programme qui s’exécute dans un processus et l’étend [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) en fournissant des informations sur le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) et un fournisseur de port personnalisé implémentent cette interface pour représenter un programme dans un processus. Le Gestionnaire de session de débogage (SDM) implémente également cette interface pour fournir des informations à [attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Le [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement retourne cette interface pour un nouveau programme. Cette interface est également utilisée en tant que paramètre pour de nombreuses méthodes sur plusieurs interfaces.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProgram3`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Exécute le programme. Le thread est retourné pour fournir les informations du débogueur threads sur lesquels l’utilisateur visualise lors de l’exécution.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Notes  
 Un programme est un conteneur de thread en cours d’exécution dans une architecture particulière de l’exécution, pendant un processus est constitué d’un ou plusieurs programmes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

