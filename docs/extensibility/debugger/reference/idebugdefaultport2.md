---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed38c530ee972e413ee98cc9d94f0f19a9b57069
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351718"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Cette interface fournit plusieurs méthodes pour accéder à serveur d’un port et les fonctionnalités de notification.

## <a name="syntax"></a>Syntaxe

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Visual Studio implémente cette interface pour représenter le port de débogage pour l’accès à des programmes. Un fournisseur de port personnalisé peut également implémenter cette interface si elle gère le débogage à distance.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un argument à des méthodes sur le [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface fournit cette interface. Appel [QueryInterface](/cpp/atl/queryinterface) sur un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface peut également obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Outre les méthodes définies dans [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtient l’interface de notification de port à partir de ce port.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtient l’interface pour le serveur qui héberge ce port.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Détermine si ce port est en cours d’exécution sur l’ordinateur local.|

## <a name="remarks"></a>Notes
 Le nom «`IDebugDefaultPort2`» est un peu trompeur, car il ne représente pas un port par défaut. Il peut être appelée « IDebugPort3 ».

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)