---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61cc6f609295022c27b18895f905e7931c834e8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876875"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Cette interface inscrit ou annule l’inscription d’un programme qui peut être débogué avec le port, qu'il s’exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge d’ajout et suppression de programmes à partir du port. Il est généralement implémentée sur le même objet qui implémente le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un appel à [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugPort2` interface retourne cette interface. En outre, un appel à [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retourne cette interface. Un moteur de débogage peut voir cette interface en tant que paramètre à [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPortNotify2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Inscrit un programme qui peut être débogué avec le port, qu'il s’exécute.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annule l’inscription d’un programme qui peut être débogué à partir du port qu'il s’exécute.|  
  
## <a name="remarks"></a>Notes  
 Sauf si un port de débogage a un moyen de savoir quand les programmes sont chargés ou déchargés, un fournisseur de port personnalisé doit implémenter cette interface. Tous les programmes qui sont chargés pour le débogage via un port particulier sont suivies à l’aide de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)