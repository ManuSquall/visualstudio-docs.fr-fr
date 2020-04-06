---
title: IDebugEngine3 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730658"
---
# <a name="idebugengine3"></a>IDebugEngine3
Représente un seul moteur de débogage (DE) qui contrôle le débogage d’un ou plusieurs modules.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un DE personnalisé (si elle prend en charge les symboles) pour activer l’état JustMyCode. Cette interface doit être implémentée par le DE si elle prend en charge les symboles et JustMyCode.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de déboque de session (SDM) pour transmettre les options utilisateur pour les emplacements à partir desquels charger des symboles. Il est également appelé à définir le GUID du moteur lorsqu’il est instantané (ce GUID est basé sur les mesures à partir du moment de l’immatriculation du moteur). Le SDM appelle également cette interface pour définir l’état JustMyCode et pour définir toutes les exceptions connues par le débbugger à un état spécifié.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), l’interface `IDebugEngine3` expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Définit le chemin ou les chemins que le DE utilisera pour rechercher des symboles de débogage.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Charge les symboles pour tous les modules qui n’ont pas encore eu leurs symboles chargés.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informe le DE des informations JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Définit le DE GUID à partir des mesures.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Définissez toutes les exceptions actuellement en suspens à un état spécifié.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
