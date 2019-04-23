---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a37ad954202910930ff06c8206e66c0594a8d1d8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107396"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Cette interface énumère les programmes en cours d’exécution dans la session de débogage actuelle.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour fournir une liste des programmes en cours de débogage par le DE.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les appels de Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) pour obtenir cette interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) n’est pas utilisé par Visual Studio.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugPrograms2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Récupère un nombre spécifié de programmes dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignore un nombre spécifié de programmes dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtient le nombre de programmes dans un énumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cette interface pour :

- Remplir le **Modules** fenêtre (en appelant [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , puis en appelant [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) sur chaque programme).

- Remplir le **attacher au processus** liste (en appelant `IDebugProcess2::EnumPrograms` , puis en appelant [QueryInterface](/cpp/atl/queryinterface) sur chaque [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour obtenir un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).

- Générer une liste DEs, qui peut déboguer chaque programme dans le processus (à l’aide de [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Appliquer des mises à jour de modifier & Continuer (ENC) pour chaque programme (en appelant IDebugProcess2::EnumPrograms, puis [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)