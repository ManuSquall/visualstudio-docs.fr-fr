---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6faa47bc107c8d00864307bdb6802908e085652
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928468"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Cette interface donne accès aux informations sur le serveur dans lequel le processus s’exécute.

## <a name="syntax"></a>Syntaxe

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir d’une interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) . Un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) peut également retourner cette interface. Cette interface est utilisée le plus souvent par un fournisseur de ports personnalisé pour lancer des programmes sur un serveur (local ou distant).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur l’interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Récupère le nom du serveur.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Récupère une version conviviale du nom du serveur|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indique aux moteurs de débogage spécifiques de s’attacher automatiquement aux processus lorsque ces processus démarrent.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Récupère un code d’erreur spécifique lorsque l’attachement automatique échoue.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crée une instance d’un moteur de débogage sur le serveur.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Récupère un indicateur qui spécifie si le serveur se trouve sur le même ordinateur que l’appelant.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Récupère une valeur indiquant le protocole utilisé pour communiquer avec le serveur.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Désactive tous les paramètres d’attachement automatique de tous les moteurs de débogage connus par ce serveur.|

## <a name="remarks"></a>Notes
 Un fournisseur de port personnalisé reçoit l’interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) sur un appel à l' [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md). L' `IDebugCoreServer3` interface peut être obtenue à partir de cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
