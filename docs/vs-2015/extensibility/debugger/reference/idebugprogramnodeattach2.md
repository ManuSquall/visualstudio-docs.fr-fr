---
title: IDebugProgramNodeAttach2 | Microsoft Docs
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
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 752d863deb3f44f0cc2a36ce6e32db879225c2c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258386"
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
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

