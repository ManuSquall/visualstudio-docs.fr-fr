---
title: IDebugEngine2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730862"
---
# <a name="idebugengine2"></a>IDebugEngine2
Cette interface représente un moteur de débogé (DE). Il est utilisé pour gérer divers aspects d’une session de débogage, de la création de points d’arrêt à la mise en place et la compensation des exceptions.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un DE personnalisé pour gérer le débogage des programmes. Cette interface doit être implémentée par le DE.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de débogage de session (SDM) pour gérer la session de débogage, y compris la gestion des exceptions, la création de points d’arrêt, et la réponse aux événements synchrones envoyés par le DE.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugEngine2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crée un enumérateur pour tous les programmes étant débogé par un DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Attache un DE à un programme.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crée un point d’arrêt en attente dans le DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Précise comment le DE doit gérer une exception donnée.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Supprime l’exception spécifiée de sorte qu’il n’est plus manipulé par le moteur de déboise.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Supprime la liste des exceptions que l’IDE a définies pour une architecture ou une langue particulière en temps de fonctionnement.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtient le GUID de la DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informe un DE que le programme spécifié a été atypiquement terminé et que le DE devrait nettoyer toutes les références au programme et envoyer un événement de destruction de programme.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Appelé par le SDM pour indiquer qu’un événement de débbug synchrone, précédemment envoyé par le DE au SDM, a été reçu et traité.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Définit le lieu de la DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Définit la racine du registre actuellement utilisée par le DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Définit une mesure.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Demande que tous les programmes étant débogé par cette exécution DE arrêter la prochaine fois l’un de leurs fils tente de courir.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
