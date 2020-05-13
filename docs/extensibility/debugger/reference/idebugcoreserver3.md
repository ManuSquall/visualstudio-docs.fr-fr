---
title: IDebugCoreServer3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732811"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Cette interface donne accès à des informations sur le serveur dans lequel le processus s’exécute.

## <a name="syntax"></a>Syntaxe

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir d’une interface [IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) peut également retourner cette interface. Cette interface est utilisée le plus souvent par un fournisseur de port personnalisé pour lancer des programmes sur un serveur (local ou distant).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes de l’interface [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetServerName (en)](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Récupère le nom du serveur.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Récupère une version amicale du nom du serveur|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indique que les moteurs de déboçons spécifiques doivent s’attacher automatiquement aux processus lorsque ces processus commencent.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Récupère un code d’erreur spécifique lorsque la fixation automatique échoue.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crée une instance d’un moteur de débogé sur le serveur.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Récupère un drapeau indiquant si le serveur est sur la même machine que l’appelant.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Récupère une valeur indiquant le protocole utilisé pour communiquer avec le serveur.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Désactive tous les paramètres d’auto-attachement pour tous les moteurs de débogé de ce serveur connaît.|

## <a name="remarks"></a>Notes
 Un fournisseur de port personnalisé reçoit l’interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) sur un appel à [l’événement](../../../extensibility/debugger/reference/idebugportevents2-event.md). L’interface `IDebugCoreServer3` peut être obtenue à partir de cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
