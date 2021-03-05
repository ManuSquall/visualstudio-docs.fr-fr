---
description: Cette interface représente un processus en cours d’exécution et ses programmes.
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2303dfef18a1abccc728d80def0de25b4e7eadd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169182"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Cette interface représente un processus en cours d’exécution et ses programmes. Cette interface existe en remplacement de plusieurs méthodes dans l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Il permet de contrôler tous les programmes du processus.

> [!NOTE]
> Les méthodes [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)et [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) sont déconseillées et ne doivent plus être utilisées. Utilisez plutôt les méthodes correspondantes sur l' `IDebugProcess3` interface.

## <a name="syntax"></a>Syntaxe

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un fournisseur de ports personnalisé pour gérer les programmes en tant que groupe. Lorsque les programmes sont gérés en tant que groupe, vous pouvez contrôler leur exécution et établir une langue pour un évaluateur d’expression. Cette interface doit être implémentée par le fournisseur de port.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée principalement par le gestionnaire de débogage de session (SDM) pour interagir avec un groupe de programmes identifiés dans ce processus.

 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Poursuit l’exécution d’un processus ou pas à pas.|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Commence l’exécution d’un processus.|
|[Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Avance d’une instruction ou d’une instruction dans le processus.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtient la raison pour laquelle le processus a été lancé pour le débogage.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Définit le langage d’hébergement afin que le moteur de débogage puisse charger l’évaluateur d’expression approprié.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Récupère la langue actuellement définie pour ce processus.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Désactive modifier & Continuer (ENC) pour ce processus.<br /><br /> Un fournisseur de port personnalisé n’implémente pas cette méthode (il doit toujours retourner `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtient l’État ENC pour ce processus.<br /><br /> Un fournisseur de port personnalisé n’implémente pas cette méthode (il doit toujours retourner `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Récupère un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
