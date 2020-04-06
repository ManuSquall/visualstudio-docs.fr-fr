---
title: IDebugPort2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725231"
---
# <a name="idebugport2"></a>IDebugPort2
Cette interface représente un port de débogé sur une machine.

## <a name="syntax"></a>Syntaxe

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour représenter un port de débogé sur une machine.

 Si le port prend en charge l’envoi d’événements portuaires, il doit également implémenter l’interface <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> pour prendre en charge une <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface qui fournit à son tour [l’interface IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Les appels vers [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) renvoient cette interface, représentant le port demandé.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugPort2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retourne le nom du port.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retourne l’identifiant du port.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retourne la demande utilisée pour créer un port (si disponible).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Retourne le fournisseur de port pour ce port.|
|[GetProcess (en)](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Renvoie une interface au processus compte tenu de l’identifiant du processus.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Énumère tous les processus en cours d’exécution sur un port.|

## <a name="remarks"></a>Notes
 Le port local donne accès à tous les processus et programmes en cours d’exécution sur la machine locale. D’autres ports peuvent représenter une connexion par câble en série à un appareil Windows CE ou une connexion réseau à un ordinateur non-DCOM. L’interface `IDebugPort2` est utilisée pour trouver le nom et l’identifiant d’un port, et énumérer tous les processus en cours d’exécution sur le port. Les installations de lancement et de résiliation des processus sur le port sont mises en œuvre dans l’interface. `IDebugPortEx2`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
