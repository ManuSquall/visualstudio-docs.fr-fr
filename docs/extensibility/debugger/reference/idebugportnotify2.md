---
title: IDebugPortNotify2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724920"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Cette interface enregistre ou dément un programme qui peut être déboqué avec le port sur lequel il fonctionne.

## <a name="syntax"></a>Syntaxe

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour soutenir l’ajout et la suppression des programmes du port. Il est généralement implémenté sur le même objet qui implémente l’interface [IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [QueryInterface](/cpp/atl/queryinterface) sur l’interface `IDebugPort2` renvoie cette interface. En outre, un appel à [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) renvoie cette interface. Un moteur de débogé peut voir cette interface comme un paramètre pour [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugPortNotify2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Enregistre un programme qui peut être déboqué avec le port sur lequel il fonctionne.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Non inscrit un programme qui peut être déboqué du port sur lequel il fonctionne.|

## <a name="remarks"></a>Notes
 À moins qu’un port de débaille ait un moyen de savoir quand les programmes sont chargés ou déchargés, un fournisseur de port personnalisé doit implémenter cette interface. Tous les programmes qui sont chargés pour débogage à travers un port particulier sont suivis à l’aide de cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
