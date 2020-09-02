---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730658"
---
# <a name="idebugengine3"></a>IDebugEngine3
Représente un moteur de débogage unique (DE) qui contrôle le débogage d’un ou plusieurs modules.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un personnalisé DE (s’il prend en charge les symboles) pour activer l’état JustMyCode. Cette interface doit être implémentée par le si elle prend en charge les symboles et JustMyCode.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de débogage de session (SDM) pour transmettre les options utilisateur pour les emplacements à partir desquels les symboles doivent être chargés. Elle est également appelée pour définir le GUID du moteur lorsqu’il est instancié (ce GUID est basé sur les métriques du moment de l’inscription du moteur). Le SDM appelle également cette interface pour définir l’état JustMyCode et pour définir toutes les exceptions connues par le débogueur à un état spécifié.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), l' `IDebugEngine3` interface expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Définit le ou les chemins d’accès que le DE utilise pour rechercher des symboles de débogage.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Charge les symboles pour tous les modules dont les symboles n’ont pas encore été chargés.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indique à l’à propos des informations DE JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Définit le GUID de à partir des métriques.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Définit toutes les exceptions actuellement en suspens à un état spécifié.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
