---
title: IDebugOutputStringEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726022"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Cette interface est envoyée par le moteur de débogé (DE) au gestionnaire de débogé de session (SDM) pour produire une chaîne.

## <a name="syntax"></a>Syntaxe

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour envoyer une chaîne à la fenêtre **de sortie** de l’IDE. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour envoyer une chaîne à la fenêtre **de sortie.** L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugOutputStringEvent2`la méthode de .

|Méthode|Description|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Obtient le message displayable.|

## <a name="remarks"></a>Notes
 Par exemple, dans le code non manipulé, la chaîne à produire peut provenir lorsque le programme `OutputDebugString` étant déboché envoie une chaîne à la fonction Win32. Cette chaîne est interceptée par le DE et envoyée `IDebugOutputStringEvent2` au SDM comme événement.

 Utilisez [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) pour envoyer un message qui nécessite une réponse de l’utilisateur.

 Utilisez [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer un message d’erreur qui ne nécessite pas de réponse.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
