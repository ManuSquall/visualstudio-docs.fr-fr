---
title: IDebugProgramNodeAttach2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permet à un nœud de programme être averti d’une tentative d’attachement au programme associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée sur la même classe qui implémente le [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface afin de recevoir une notification d’une opération d’attachement et pour fournir la possibilité d’annuler l’opération d’attachement.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Obtenez cette interface en appelant le `QueryInterface` méthode dans un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objet. Le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode doit être appelée avant la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode afin de donner le nœud programme possibilité d’arrêter le processus d’attachement.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|S’attache au programme associé ou diffère du processus d’attachement à la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).|  
  
## <a name="remarks"></a>Notes  
 Cette interface est l’alternative recommandée à la fonctionnalité déconseillée [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) (méthode). Tous les moteurs de débogage sont toujours chargés avec les `CoCreateInstance` de fonction, autrement dit, ils sont instanciés à l’extérieur de l’espace d’adressage du programme en cours de débogage.  
  
 Si une précédente implémentation de la `IDebugProgramNode2::Attach_V7` simplement définition de la méthode la `GUID` du programme en cours de débogage, puis uniquement les [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode doit être implémentée.  
  
 Si une précédente implémentation de la `IDebugProgramNode2::Attach_V7` méthode utilisé l’interface de rappel qui a été fourni, puis cette fonctionnalité doit être déplacé vers une implémentation de la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode) et le `IDebugProgramNodeAttach2` n’est pas le cas de l’interface doivent être implémentées.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Joindre](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)