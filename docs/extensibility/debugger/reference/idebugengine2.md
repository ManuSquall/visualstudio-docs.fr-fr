---
description: Cette interface représente un moteur DE débogage (DE).
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066150"
---
# <a name="idebugengine2"></a>IDebugEngine2
Cette interface représente un moteur DE débogage (DE). Il est utilisé pour gérer différents aspects d’une session de débogage, de la création de points d’arrêt à la définition et à l’effacement des exceptions.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un personnalisé DE pour gérer le débogage des programmes. Cette interface doit être implémentée par le DE.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de débogage de session (SDM) pour gérer la session de débogage, y compris la gestion des exceptions, la création de points d’arrêt et la réponse aux événements synchrones envoyés par le.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEngine2` .

|Méthode|Description|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crée un énumérateur pour tous les programmes en cours de débogage par un DE.|
|[Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Joint un DE à un programme.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crée un point d’arrêt en attente dans le DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Spécifie comment le DE doit gérer une exception donnée.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Supprime l’exception spécifiée afin qu’elle ne soit plus gérée par le moteur de débogage.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Supprime la liste des exceptions que l’IDE a définies pour une architecture ou un langage d’exécution spécifique.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtient le GUID du DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informe un DE que le programme spécifié a été arrêté de manière atypique et que le DE doit nettoyer toutes les références au programme et envoyer un événement de destruction de programme.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Appelé par le SDM pour indiquer qu’un événement de débogage synchrone, précédemment envoyé par le DE à SDM, a été reçu et traité.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Définit les paramètres régionaux de l’DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Définit la racine de Registre actuellement utilisée par le.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Définit une métrique.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Demande que tous les programmes débogués par ce cessent d’être exécutés la prochaine fois que l’un de leurs threads tente de s’exécuter.|

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
