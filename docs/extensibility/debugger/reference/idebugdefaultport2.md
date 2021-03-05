---
description: Cette interface fournit plusieurs méthodes pour accéder aux fonctionnalités de serveur et de notification d’un port.
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5ec637daa197574710978af7cb22195c969f48b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154416"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Cette interface fournit plusieurs méthodes pour accéder aux fonctionnalités de serveur et de notification d’un port.

## <a name="syntax"></a>Syntaxe

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface pour représenter le port de débogage pour l’accès aux programmes. Un fournisseur de port personnalisé peut également implémenter cette interface s’il gère le débogage distant.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un argument des méthodes sur l’interface [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) fournit cette interface. L’appel de [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) peut également obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 En plus des méthodes définies dans [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtient l’interface de notification de port à partir de ce port.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtient l’interface du serveur qui héberge ce port.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Détermine si ce port est en cours d’exécution sur l’ordinateur local.|

## <a name="remarks"></a>Notes
 Le nom « `IDebugDefaultPort2` » est un peu d’un impropre, car il ne représente pas un port par défaut. Elle peut être appelée « IDebugPort3 ».

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
