---
description: Cette interface est utilisée pour demander au gestionnaire de débogage de session (SDM) s’il doit s’arrêter à l’emplacement de code actuel.
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73d881b1aef09d13d7b7138348d5198c8322694
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085011"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Cette interface est utilisée pour demander au gestionnaire de débogage de session (SDM) s’il doit s’arrêter à l’emplacement de code actuel.

## <a name="syntax"></a>Syntaxe

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) implémente cette interface pour prendre en charge le pas à pas détaillé dans le code source. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface).

 L’implémentation de cette interface doit communiquer l’appel de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) par le SDM au moteur de débogage. Par exemple, cela peut être fait avec un message publié dans le thread de gestion des messages du moteur de débogage, ou l’objet qui implémente cette interface peut contenir une référence au moteur de débogage et rappeler dans le moteur de débogage avec l’indicateur passé dans `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Notes pour les appelants
 La valeur DE peut envoyer cette méthode chaque fois que le DE est invité à poursuivre l’exécution et que l’exécution du code pas à pas. Cet événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugCanStopEvent2` .

|Méthode|Description|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtient la raison de cet événement.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Spécifie si le programme en cours de débogage doit s’arrêter à l’emplacement de cet événement (et envoyer un événement qui décrit la raison de l’arrêt) ou simplement continuer l’exécution.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtient le contexte de document qui décrit l’emplacement de cet événement.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtient le contexte de code qui décrit l’emplacement de cet événement.|

## <a name="remarks"></a>Notes
 Le DE envoie cette interface si l’utilisateur effectue un pas à pas détaillé dans une fonction et que le DE ne trouve pas d’informations de débogage ou si des informations de débogage existent, mais que ne sait pas si le code source peut être affiché pour cet emplacement.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
