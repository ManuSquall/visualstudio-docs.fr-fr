---
title: IEnumDebugProcesses2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715760"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Cette interface énumère les processus en cours d’exécution sur un port de déboguer.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour fournir une liste des processus en cours d’exécution sur un port.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugProcesses2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Récupère un nombre précis de processus dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Passe un nombre précis de processus dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtient le nombre de processus dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cette interface pour remplir la fenêtre **Processes.**

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
