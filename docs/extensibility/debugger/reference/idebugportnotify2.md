---
description: Cette interface inscrit ou annule l’inscription d’un programme pouvant être débogué avec le port sur lequel il s’exécute.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 759be0ff57da7c6bb65ed6ca8191720f835b894a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169338"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Cette interface inscrit ou annule l’inscription d’un programme pouvant être débogué avec le port sur lequel il s’exécute.

## <a name="syntax"></a>Syntaxe

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge l’ajout et la suppression de programmes du port. Elle est généralement implémentée sur le même objet qui implémente l’interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [QueryInterface](/cpp/atl/queryinterface) sur l' `IDebugPort2` interface retourne cette interface. En outre, un appel à [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) retourne cette interface. Un moteur de débogage peut voir cette interface en tant que paramètre de [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugPortNotify2` .

|Méthode|Description|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Inscrit un programme pouvant être débogué avec le port sur lequel il s’exécute.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annule l’inscription d’un programme pouvant être débogué à partir du port sur lequel il s’exécute.|

## <a name="remarks"></a>Notes
 À moins qu’un port de débogage n’ait un moyen de savoir quand des programmes sont chargés ou déchargés, un fournisseur de port personnalisé doit implémenter cette interface. Tous les programmes chargés pour le débogage via un port particulier sont suivis à l’aide de cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
