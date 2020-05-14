---
title: IDebugProgramNodeAttach2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721819"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permet à un nœud de programme d’être avisé d’une tentative de s’attacher au programme associé.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée sur la même classe qui implémente l’interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) afin de recevoir la notification d’une opération de jointage et de fournir la possibilité d’annuler l’opération de jointage.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Obtenez cette interface `QueryInterface` en appelant la méthode dans un objet [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) La méthode [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être appelée avant la méthode [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) pour donner au nœud de programme une chance d’arrêter le processus d’attachement.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Attache au programme associé ou reporte le processus d’attachement à la méthode [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Notes
 Cette interface est l’alternative préférée à la méthode [de Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) dépréciée. Tous les moteurs débogé `CoCreateInstance` sont toujours chargés avec la fonction, c’est-à-dire, ils sont instantanés en dehors de l’espace d’adresse du programme étant débogé.

 Si une mise `IDebugProgramNode2::Attach_V7` en œuvre `GUID` antérieure de la méthode était simplement l’établissement du programme étant débogé, alors seule la méthode [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être mis en œuvre.

 Si une implémentation précédente de la `IDebugProgramNode2::Attach_V7` méthode utilisait l’interface de rappel qui a été fournie, alors cette fonctionnalité doit être déplacée vers une implémentation de la méthode [Joindre](../../../extensibility/debugger/reference/idebugengine2-attach.md) et l’interface `IDebugProgramNodeAttach2` n’a pas besoin d’être implémentée.

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
