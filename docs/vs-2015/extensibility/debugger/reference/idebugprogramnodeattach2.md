---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 580d4d2432a957bae8c590b3590a11b1a0b5e84e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938460"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permet à un nœud de programme être averti d’une tentative d’attachement au programme associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée sur la même classe qui implémente le [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface afin de recevoir des notifications d’une opération d’attachement et de fournir la possibilité d’annuler l’opération d’attachement.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Obtenez cette interface en appelant le `QueryInterface` méthode dans un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objet. Le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode doit être appelée avant la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode pour le nœud de programme une occasion pour arrêter le processus d’attachement.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Est attaché au programme associé ou diffère le processus d’attachement à la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).|  
  
## <a name="remarks"></a>Notes  
 Cette interface est l’alternative recommandée à la fonctionnalité déconseillée [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) (méthode). Tous les moteurs de débogage sont toujours chargés avec le `CoCreateInstance` de fonction, autrement dit, ils sont instanciés en dehors de l’espace d’adressage du programme en cours de débogage.  
  
 Si une précédente implémentation de la `IDebugProgramNode2::Attach_V7` méthode a été définissant simplement le `GUID` du programme en cours de débogage, puis uniquement le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode doit être implémentée.  
  
 Si une précédente implémentation de la `IDebugProgramNode2::Attach_V7` méthode utilisé l’interface de rappel qui a été fournie, alors que cette fonctionnalité doit être déplacé vers une implémentation de la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode) et le `IDebugProgramNodeAttach2` n’est pas le cas de l’interface doivent être implémentées.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
