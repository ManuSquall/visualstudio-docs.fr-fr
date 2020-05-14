---
title: IEnumDebugPrograms2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715567"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Cette interface énumère les programmes en cours d’exécution dans la session de débogé actuelle.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour fournir une liste de programmes en cours de débbugged par le DE.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) pour obtenir cette interface. [EnumPrograms n’est](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) pas utilisé par Visual Studio.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugPrograms2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Récupère un nombre précis de programmes dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Passe un nombre précis de programmes dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtient le nombre de programmes dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cette interface pour :

- Remplissez la fenêtre **Modules** (en appelant [EnumPrograms,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) puis en appelant [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) sur chaque programme).

- Remplissez la liste **d’attache à la procédure** (en appelant `IDebugProcess2::EnumPrograms` puis en appelant [QueryInterface](/cpp/atl/queryinterface) sur chaque interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour obtenir une interface [IDebugEngineProgram2).](../../../extensibility/debugger/reference/idebugengineprogram2.md)

- Générer une liste de DEs qui peuvent déboiffer chaque programme dans le processus (en utilisant [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Appliquez les mises à jour Edit and Continue (ENC) à chaque programme (en appelant IDebugProcess2::EnumPrograms, puis en appelant [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
