---
title: IDebugCanStopEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734514"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Cette interface est utilisée pour demander au gestionnaire de débogé de session (SDM) s’il faut s’arrêter à l’emplacement actuel du code.

## <a name="syntax"></a>Syntaxe

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour prendre en charge le passage du code source. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette `IDebugEvent2` interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface).

 La mise en œuvre de cette interface doit communiquer l’appel de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) par le SDM au moteur de débogé. Par exemple, cela peut être fait avec un message posté sur le fil de manipulation de message du moteur de débog ou l’objet de `IDebugCanStopEvent2::CanStop`mise en œuvre de cette interface pourrait tenir une référence au moteur de débogé et rappeler dans le moteur de débogé avec le drapeau passé en .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE peut envoyer cette méthode chaque fois que le DE est invité à continuer l’exécution et le DE est en marche à travers le code. Cet événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il s’est joint au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugCanStopEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtient la raison de cet événement.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Précise si le programme qui est débogé doit s’arrêter à l’endroit de cet événement (et envoyer un événement qui décrit la raison de l’arrêt) ou tout simplement continuer l’exécution.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtient le contexte de document qui décrit l’emplacement de cet événement.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtient le contexte de code qui décrit l’emplacement de cet événement.|

## <a name="remarks"></a>Notes
 Le DE envoie cette interface si l’utilisateur entre dans une fonction et le DE ne trouve aucune information de débbug là-bas ou de déboiffer des informations existe, mais le DE ne sait pas si le code source peut être affiché pour cet emplacement.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
