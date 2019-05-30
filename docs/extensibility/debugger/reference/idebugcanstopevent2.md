---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab364b426005c838072fabc1a3c7ed2f7d64ac6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337341"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Cette interface est utilisée pour demander le Gestionnaire de session de débogage (SDM) s’il faut arrêter à l’emplacement de code actuel.

## <a name="syntax"></a>Syntaxe

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour prendre en charge dans le code source. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface).

 L’implémentation de cette interface doit communiquer d’appel du SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) au moteur de débogage. Par exemple, cela est possible avec un message publié sur le thread de gestion de messages du moteur de débogage ou de l’objet qui implémente cette interface peut contenir une référence au moteur de débogage et effectuer un rappel dans le moteur de débogage avec l’indicateur passé dans `IDebugCanStopEvent2::CanStop`.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE peut envoyer cette méthode chaque fois que l’Allemagne est invité à continuer l’exécution et l’Allemagne est parcours du code. Cet événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugCanStopEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtient la raison de cet événement.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Spécifie si le programme en cours de débogage doit s’arrêter à l’emplacement de cet événement (et envoyer un événement qui décrit la raison de l’arrêt) ou simplement poursuivre l’exécution.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtient le contexte de document qui décrit l’emplacement de cet événement.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtient le contexte de code qui décrit l’emplacement de cet événement.|

## <a name="remarks"></a>Notes
 Le D’envoie cette interface si les étapes de l’utilisateur dans une fonction et DE ne recherche il aucune information de débogage ou les informations de débogage existent mais que l’Allemagne ne sait pas si le code source peut être affiché pour cet emplacement.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)