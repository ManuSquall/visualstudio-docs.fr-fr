---
title: IDebugPortEvents2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725177"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Cette interface informe un auditeur (généralement le gestionnaire de débogé de session [SDM] ou un moteur de débogé) de la création et de la destruction des procédés et des programmes sur un port particulier. Ces informations peuvent être utilisées pour présenter une vue en temps réel des processus et des programmes en cours d’exécution sur le port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente généralement cette interface pour recevoir des notifications sur la création et la destruction du programme. Un moteur de débogé peut également implémenter cette interface pour écouter de tels événements portuaires.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Toutes les interfaces [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) peuvent <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> être demandées pour une interface. Ensuite, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> la `IDebugPortEvents2` méthode pour <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> est appelé <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> dans l’interface pour obtenir une interface. Enfin, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> la méthode <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> de l’interface est appelée pour envoyer les événements par la méthode [De l’événement.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugPortEvents2`la méthode de .

|Méthode|Description|
|------------|-----------------|
|[Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envoie des événements qui décrivent la création et la destruction de processus et de programmes sur le port.|

## <a name="remarks"></a>Notes
 `IDebugPortEvents2`est également utilisé par le SDM pour déboguer les programmes qui fonctionnent dans un processus qui est déjà en cours de débbugged.

 Les événements portuaires sont transmis au SDM par cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
