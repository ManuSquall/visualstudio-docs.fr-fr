---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1b131679a287fb555fcf2a78a803c77457d47ca
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343513"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permet à un moteur de débogage remplacer le comportement par défaut de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur lorsque vous arrêtez une session de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par les moteurs de débogage. Il est utile pour les hôtes qui peuvent créer et détruire de plusieurs programmes pendant la durée de vie d’un processus.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugProgramDestroyEventFlags2`.

|Méthode|Description|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Récupère le programme détruire des indicateurs.|

## <a name="remarks"></a>Notes
 Le comportement par défaut de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur consiste à revenir en arrière en mode Création après que tous les programmes ont envoyées à un programme événement de destruction. Cette interface permet à un moteur de débogage modifier ce comportement.

## <a name="requirements"></a>Configuration requise
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll