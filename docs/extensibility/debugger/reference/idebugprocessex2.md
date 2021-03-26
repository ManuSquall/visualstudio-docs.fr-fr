---
description: Cette interface permet au gestionnaire de débogage de session (SDM) de notifier à un processus qu’il est attaché ou détaché du processus.
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bd22a779cd0a474b5df03d2315402dbe1a25239
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081514"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Cette interface permet au gestionnaire de débogage de session (SDM) de notifier à un processus qu’il est attaché ou détaché du processus.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que l’interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) afin de :

- Prendre en charge le suivi des sessions connectées à un processus

- Prendre en charge l’attachement automatique sur plusieurs moteurs de débogage

  Le fournisseur de port personnalisé peut implémenter cette interface s’il le souhaite.

## <a name="notes-for-callers"></a>Notes pour les appelants

- Le SDM appelle [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProcess2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProcessEx2` .

|Méthode|Description|
|------------|-----------------|
|[Attacher](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informe le processus qu’une session est en train de déboguer le processus.|
|[Détacher](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informe le processus qu’une session n’est plus en train de déboguer le processus.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Ajoute des nœuds de programme pour une liste de moteurs de débogage.|

## <a name="remarks"></a>Notes
 Cette interface est privée entre le SDM et le processus.

## <a name="requirements"></a>Spécifications
 En-tête : Portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
