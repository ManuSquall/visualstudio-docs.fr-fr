---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74a25e4eefe260dd61dc951118cdb6390a61b52d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898502"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permet à un nœud de programme d’être averti d’une tentative d’attachement au programme associé.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée sur la même classe qui implémente l’interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) afin de recevoir la notification d’une opération d’attachement et de fournir une opportunité d’annuler l’opération d’attachement.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Obtenez cette interface en appelant la `QueryInterface` méthode dans un objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . La méthode [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être appelée avant la méthode [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) pour permettre au nœud de programme d’arrêter le processus d’attachement.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Joint au programme associé ou diffère le processus d’attachement à la méthode d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Remarques
 Cette interface est l’alternative recommandée à la méthode de [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) déconseillée. Tous les moteurs de débogage sont toujours chargés avec la `CoCreateInstance` fonction, autrement dit, ils sont instanciés en dehors de l’espace d’adressage du programme en cours de débogage.

 Si une implémentation précédente de la `IDebugProgramNode2::Attach_V7` méthode définissait simplement le `GUID` du programme en cours de débogage, seule la méthode [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être implémentée.

 Si une implémentation précédente de la `IDebugProgramNode2::Attach_V7` méthode utilisait l’interface de rappel fournie, cette fonctionnalité doit être déplacée vers une implémentation de la méthode d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) et il `IDebugProgramNodeAttach2` n’est pas nécessaire d’implémenter l’interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
