---
title: IDebugErrorEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00fd8b4b42f11d18958f8a969bc4ccd58754ab93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730000"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Cette interface spécifie un message d’erreur à signaler à l’utilisateur.

## <a name="syntax"></a>Syntaxe

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour signaler les erreurs comme des messages lisibles par l’homme. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler une erreur. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme étant débogé.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|`GetErrorMessage`|Retourne une erreur comme une chaîne lisible par l’homme.|

## <a name="remarks"></a>Notes
 Si le moteur de débogé rencontre une erreur, il peut utiliser cette interface pour signaler le message via Visual Studio à l’utilisateur.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
