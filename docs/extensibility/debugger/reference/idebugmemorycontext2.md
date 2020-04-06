---
title: IDebugMemoryContext2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727431"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Cette interface représente une position dans l’espace d’adresse de la machine en cours d’exécution du programme étant débogé.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter une adresse en mémoire.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) renvoie cette interface. En outre, les appels pour [ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) et [soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retourner de nouvelles copies de cette interface après l’opération arithmétique appropriée a été appliquée.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugMemoryContext2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtient le nom affichage utilisateur pour ce contexte.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtient des informations qui décrivent ce contexte.|
|[Ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Ajoute une valeur spécifiée à l’adresse du contexte actuel pour créer un nouveau contexte.|
|[Soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Soustraite une valeur spécifiée de l’adresse du contexte actuel pour créer un nouveau contexte.|
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compare deux contextes de la manière indiquée par la comparaison des drapeaux.|

## <a name="remarks"></a>Notes
 La fenêtre **Mémoire** de Visual Studio appelle [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) pour obtenir l’interface `IDebugMemoryContext2` qui contient l’expression évaluée utilisée pour l’adresse mémoire. Ce contexte est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) pour spécifier l’adresse à lire ou à écrire.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
