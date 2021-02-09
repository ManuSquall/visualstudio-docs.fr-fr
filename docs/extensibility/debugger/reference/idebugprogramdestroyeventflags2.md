---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd43b93f8a74e0e1fcb12ac9be4da47142a79519
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848219"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permet à un moteur de débogage de substituer le comportement par défaut de l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur quand vous terminez une session de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les moteurs de débogage. Elle est utile pour les hôtes qui peuvent créer et détruire plusieurs programmes pendant la durée de vie d’un processus.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugProgramDestroyEventFlags2` .

|Méthode|Description|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Récupère les indicateurs de destruction du programme.|

## <a name="remarks"></a>Remarques
 Le comportement par défaut de l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur consiste à revenir au mode création après que tous les programmes ont envoyé un événement de destruction de programme. Cette interface permet à un moteur de débogage de modifier ce comportement.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
